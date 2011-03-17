---
layout: post
title: MailChimp Subscriber Count Service
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

<div id="search">
Filter by name:
</div>

<ul id="list">
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=54c5b9303b">Boston StartupDigest Jobs</a> - 2,022 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=a4294c263c">Boston StartupDigest</a> - 3,342 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=b6635e37e35fa5eff0c2a947a&id=a63f24d068">DevOps</a> - 832 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=dbe3ff5e1d2dd2af18cddb197&id=0905ebf33a">FareCompare</a> - 1,175 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=87be63fd80fde3e54241357c8&id=2bc973df77">hackerByte</a> - 142 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=d501d61627659be31f006dc80&id=9850ea9d48">Hipmunk</a> - 261 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=38d0a9f3a3cc16864784086bf&id=46bc7fde62">Jason Nation</a> - 22,295 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=0618f6a79d6bb9675f313ceb2&id=596bcf37c5">Javascript Weekly</a> - 4,504 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=14abd0ef4f">LA StartupDigest Jobs</a> - 2,488 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=544c942d83">LA StartupDigest</a> - 3,771 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=d6fd272142">London StartupDigest Jobs</a> - 2,276 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=0aa48cc2ac">London StartupDigest</a> - 3,859 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=ae7d9b999f4ee1793cafe3ecf&id=c48e2e2fa4">MassArt</a> - 1,267 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=f0dd695756">NYC StartupDigest Jobs</a> - 4,011 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=f13023b675">NYC StartupDigest</a> - 7,751 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=6668d9eeefc9962d2f433dceb&id=72f59191ee">Photojojo</a> - 146,930 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=f5a0df2d9082c86e808468c10&id=9fbeb5d667">ReadWriteWeb</a> - 15,572 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=906594042ce8669084b92c572&id=0f4f7807d2">RetailMeNot</a> - 322,752 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=0618f6a79d6bb9675f313ceb2&id=d9d24eba5b">Ruby Weekly</a> - 4,317 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=7f2dca86c5">Seattle StartupDigest Jobs</a> - 782 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=2c69e1d240">Seattle StartupDigest</a> - 2,172 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=e1343c1a66">Silicon Valley StartupDigest Jobs</a> - 5,524 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=f459eaf4db&id=b4f52d8716">Spark Labs</a> - 3,036 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=92be899ef5a892c60b4a6cd97&id=62dc6ea1a0">StartupDigest Reading List</a> - 12,667 subscribers</li>
<li><a href="http://us1.campaign-archive1.com/home/?u=07487d1456302a286cf9c4ccc&id=934d447288">Ted</a> - 515,462 subscribers</li>
<li><a href="http://us2.campaign-archive1.com/home/?u=4b31e3f858a9b28673cf325a4&id=3ac92de6ac">Teen Today</a> - 39,439 subscribers</li>
</ul>
