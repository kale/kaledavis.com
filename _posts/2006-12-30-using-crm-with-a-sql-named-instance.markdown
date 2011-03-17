--- 
layout: post
title: Using CRM with a SQL named instance
---
If you want to use CRM 3.0 with a named SQL instance you first have to disable the Environmental Diagnostics Wizard (EDW).  How to do this?  I couldn't find a way except for a couple <a title="Mid-Atlantic CRM" href="http://blogs.msdn.com/midatlanticcrm/archive/2006/06/23/Name-your-Instance-SQL-Instance-that-is-in-Microsoft-CRM-3.aspx">blogs</a>/<a title="CRM Newsgroup" href="http://groups.google.com/group/microsoft.public.crm.deployment/browse_thread/thread/31c06c54730988df/a3f41f7a480543d4%23a3f41f7a480543d4">newsgroups</a> pointing me to a support call with Microsoft.  The Microsoft CRM Support Team might not like me posting this simple solution, but I think it is crazy that we got charged a support call for something like this and hopefully my post can prevent someone else from being on hold for two hours.

To disable it, you simply open RegEdit on the CRM server, browse to the MSCRM key at HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> MSCRM and add the DWORD "IgnoreChecks" and give a value of 1.

You will have to reinstall CRM on the box and reconfigure what SQL server/instance you want to use there.  You will get to the screen that has the warnings/errors, and the SQL line item will still give you an warning/error, but with the registry edit you can still click the Next button to proceed (without EDW disabled you can't proceed).  After finishing the install you can delete the registry entry you added.

*As a disclaimer: backup everything, don't do this on your production box, and if you're unsure about any of this call MS support!*
