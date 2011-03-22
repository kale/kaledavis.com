---
layout: post
title: Killing Windows Services that hang on "STOPPING"
---
Although rare, sometimes a Windows Service can hang while stopping or restarting. This happened to me yesterday on one of my SharePoint servers and thought I would write-up a quick note in case I ever need it again. In my case the Office SharePoint Search Service had stopped responding and when I tried to restart the service it hung on "STOPPING". A reboot would of fixed it, but that isn't an option for a production server usually.

First, find the service name. You can do that by looking at the properties of the particular service in services.msc. Next you can use the [SC](http://technet.microsoft.com/en-us/library/bb490995.aspx) command with queryex to find the PID for that service and then use [taskkill](http://technet.microsoft.com/en-us/library/bb491009.aspx) to kill the service.

{% highlight bash %}
sc queryex osearch

taskkill /PID 2056 /F
{% endhighlight %}


*Couple notes* - the /F flag is for forcing the service to stop. Try it first without the /F. A service hanging on "STOPPING" is usually a bad sign, so you may want to figure out why this is happening before doing this.
