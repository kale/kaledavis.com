---
layout: post
title: "Exporting Data From MongoHQ"
published: true
---

{% highlight bash %}
mongodump -h temple.mongohq.com:27043 -d database_name -u username -p password -o location_to_copy_to
{% endhighlight %}
