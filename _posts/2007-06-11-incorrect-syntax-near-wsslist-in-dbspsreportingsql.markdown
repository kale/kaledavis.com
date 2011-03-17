--- 
layout: post
title: Incorrect syntax near 'WSSList' in dbSPSReporting.sql
---
Have you tried to use the [SQL Server 2005 Report Pack for SPS](http://www.microsoft.com/downloads/details.aspx?familyid=d81722ce-408c-4fb6-a429-2a7ecd62f674&displaylang=en)? I had used the previous version of this for SQL 2000 last year, but hadn't used it for a while. I remember having issues with the install of that previous version, and sure enough I had more issues this time as well.

Here is the error message you will see when you run the dbSPSReporting.sql script:

    Msg 102, Level 15, State 1, Procedure usp_Insert_FactWSS, Line 57 Incorrect syntax near 'WSSList'.
    Cannot add rows to sys.sql_dependencies for the stored procedure because it depends on the missing
    table 'usp_Insert_FactWSS'. The stored procedure will still be created; however, it cannot be
    successfully executed until the table exists.

The problem is there is a missing comma after WSSDoc nvarchar(255):

{% highlight sql %}
Create table dbo.tblTempWSS_ToFactLoad ( WSSFactID bigint identity not null Primary Key, 
  SiteGUID uniqueidentifier, WebGUID uniqueidentifier, -- WSSDate datetime, -- Fix for 
  Bug #: 403546 WSSDate smalldatetime, WSSTime nvarchar(8), --WSSUser nvarchar(150), --Fix 
  for Bug #: 403546 WSSUser nvarchar(255), --WSSDoc nvarchar(50), --Fix for Bug #: 403546 
  WSSDoc nvarchar(255) WSSList uniqueidentifier
{% endhighlight %}

Simply add the comma before you run the SQL script and everything will work fine. I find it very ironic that the new bug is right below the "Fix for Bug" comment that dealt with the previous problems in the first version. Bugs often introduce other bugs, but you would think something released for a Windows administrator would be checked a little closer. 
