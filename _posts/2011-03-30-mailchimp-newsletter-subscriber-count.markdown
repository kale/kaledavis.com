---
layout: post
title: How To Find Newsletter Subscriber Counts (if they use MailChimp) 
---
<style> 
#search {
       margin: 15px 0 15px 0;
}
.filterform {
width:220px;
      font-size:12px;
display:block;
}
.filterform input {
  -moz-border-radius:5px;
  border-radius:5px;
  -webkit-border-radius:5px;
}
</style> 
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js"></script> 
<script> 

(function ($) {
 // custom css expression for a case-insensitive contains()
 jQuery.expr[':'].Contains = function(a,i,m){
 return (a.textContent || a.innerText || "").toUpperCase().indexOf(m[3].toUpperCase())>=0;
 };

 function listFilter(header, list) { // header is any element, list is an unordered list
 // create and add the filter form to the header
 var form = $("<form>").attr({"class":"filterform","action":"#"}),
 input = $("<input>").attr({"class":"filterinput","type":"text"});
 $(form).append(input).appendTo(header);

 $(input)
 .change( function () {
   var filter = $(this).val();
   if(filter) {
   // this finds all links in a list that contain the input,
   // and hide the ones not containing the input while showing the ones that do
   $(list).find("a:not(:Contains(" + filter + "))").parent().slideUp();
   $(list).find("a:Contains(" + filter + ")").parent().slideDown();
   } else {
   $(list).find("li").slideDown();
   }
   return false;
   })
.keyup( function () {
    // fire the above change event after every letter
    $(this).change();
    });
 }

 //ondomready
 $(function () {
     listFilter($("#search"), $("#list"));
     });
}(jQuery));
</script> 

*A week later and MailChimp has [fixed](http://blog.mailchimp.com/new-chiclet-and-badge-designs/) this by allowing you to turn off the chiclet feature... they are some fast monkeys! So with that said this article will only apply to anyone who has left their privacy setting to "public", which would most likely be any newsletter that already exists as of 4/1/11.*

Did you know that the [Ted](http://www.ted.com) newsletter has over a half million subscribers? I find that impressive especially after starting my own newsletter, <a href="http://www.hackernewsletter.com">Hacker Newsletter</a>, and seeing just how tough it is to get subscribers. Every week I get feedback on how great and useful my newsletter is and always see +50% open rates, but penetrating inboxes is a lot harder than I had imagined (but a fun challenge!). I started wondering how other newsletters were doing and although some publish there subscriber counts most don't. It just took me a minute to realize that if they were using <a href="http://eepurl.com/EtWV">MailChimp</a> like I am, all I would need to figure out is how the subscriber count javascript chicklet that MailChimp provides works.

That turned out to be very easy since MailChimp uses two parameter variables to track everything: u and id. So to find those I just needed to either sign-up for their newsletter or, better yet, just find any MailChimp related links on their websites (like for the signup form or archives link) to find those parameters.

Using <a href="http://www.hackernewsletter.com">Hacker Newsletter</a> as an example:

![Hacker Newsletter Javascript Chicklet](/images/posts/hnl_mailchimp_chicklet.png)

That is created by adding the following javascript to your page:

{% highlight javascript %}
<div class="chimpchiclet">
  <script language="JavaScript"
  src="http://us1.list-manage.com/subscriber-count?b=2&u=faa8eb4ef3a111cef92c4f3d4&id=e505c88a2e"
  type="text/javascript"></script>
</div>
{% endhighlight %}

<br/>

So to find the count for any newsletter you just need to find **u**, **id**, and the server it is located on, which in my case is **us1** (us2 being the other one that I have seen). Plug those into the URL in the javascript code above and open in your browser to see the number... or see below for an easier way to do this.

I love <a href="http://eepurl.com/EtWV">MailChimp</a> and highly recommend them as they provide a really great service that is just plain fun to use. On top of that, the ability to start using them for free while your list is small (currently < 2000 subscribers) made it possible for me to start my newsletter. It does seem like they need to come up with a better way of doing this though, or at least let customers clearly know that their subscriber count is public.

<p style="font-weight: bold; padding: 10px; background: #FDD825">Do you want to find out how many subscribers any MailChimp powered newsletter has? If so, forward one of their newsletters to newsletter@simplerise.com. I have a simple script that will process it and email you back the count and add it to this page. If they don't use MailChimp it will let you know that as well.</p>

<h2>Popular Newsletter Subscriber Counts (as of 3/30/11)</h2>
<div id="search">
Filter by name:
</div>

<ul id="list">
<li><a href="http://us1.campaign-archive1.com/home/?u=07487d1456302a286cf9c4ccc&id=934d447288">Ted</a> - 512,966 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=906594042ce8669084b92c572&id=0f4f7807d2">RetailMeNot</a> - 325,807 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=6668d9eeefc9962d2f433dceb&id=72f59191ee">Photojojo</a> - 147,769 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=4b31e3f858a9b28673cf325a4&id=3ac92de6ac">Teen Today</a> - 39,264 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=38d0a9f3a3cc16864784086bf&id=46bc7fde62">Jason Nation</a> - 22,349 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=f5a0df2d9082c86e808468c10&id=9fbeb5d667">ReadWriteWeb</a> - 15,381 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=62dc6ea1a0">StartupDigest Reading List</a> - 13,803 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=2d5473bd832b12ecd4d0c6963&id=8a02a5a028">Om Says</a> - 13,676 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=2d5473bd832b12ecd4d0c6963&id=8a02a5a028">GigaOM Daily Newsletter for Tuesday</a> - 13,676 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=3a5a3fb1ad250e247bde9f42d&id=4ae03b8d6f">Tenth Amendment</a> - 11,450 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=6cd557f316f6c6b5deccf9bc0&id=fa1ece381d">thinkvitamin</a> - 11,346 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=f13023b675">NYC StartupDigest</a> - 8,059 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=e1343c1a66">Silicon Valley StartupDigest Jobs</a> - 6,045 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=0618f6a79d6bb9675f313ceb2&id=596bcf37c5">Javascript Weekly</a> - 4,784 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=0618f6a79d6bb9675f313ceb2&id=d9d24eba5b">Ruby Weekly</a> - 4,478 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=f0dd695756">NYC StartupDigest Jobs</a> - 4,378 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=0aa48cc2ac">London StartupDigest</a> - 3,993 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=2889002ad89d45ca21f50ba46&id=689d00e31c">Now I Know</a> - 3,915 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=544c942d83">LA StartupDigest</a> - 3,844 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=a4294c263c">Boston StartupDigest</a> - 3,443 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=f459eaf4db&id=b4f52d8716">Spark Labs</a> - 3,036 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=14abd0ef4f">LA StartupDigest Jobs</a> - 2,701 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=d6fd272142">London StartupDigest Jobs</a> - 2,428 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=2c69e1d240">Seattle StartupDigest</a> - 2,225 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=54c5b9303b">Boston StartupDigest Jobs</a> - 2,182 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=ae7d9b999f4ee1793cafe3ecf&id=c48e2e2fa4">MassArt</a> - 1,267 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=dbe3ff5e1d2dd2af18cddb197&id=0905ebf33a">FareCompare</a> - 1,214 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=7f2dca86c5">Seattle StartupDigest Jobs</a> - 904 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=b6635e37e35fa5eff0c2a947a&id=a63f24d068">DevOps</a> - 886 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=25c0f3189b58b697b3da13e3c&id=943136c5b5">Breakfast with Champions</a> - 794 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=faa8eb4ef3a111cef92c4f3d4&id=e505c88a2e">Hacker Newsletter</a> - 613 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=279b20f77e1a261164154c446&id=40b6e2cb5a">Subtraction.com</a> - 596 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=72f68dcee17c92724bc7822fb&id=2f0470315b">NoSQL</a> - 501 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=700201bdc3d3c2f8799341868&id=dbd08efebd">Idea Bing</a> - 368 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=d501d61627659be31f006dc80&id=9850ea9d48">Hipmunk</a> - 302 subscribers</li>
</ul>
