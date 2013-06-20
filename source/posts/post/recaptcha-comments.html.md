---
title: ReCaptcha Comments
date: 2010-05-18 08:16 CDT
tags: modx, commenting, recaptcha
teaser: A few people have asked how I did the reCaptcha support in my comments section of the site. It was actually pretty simple, and didn't require any coding at all. Thanks Quip.
---

<p>This site's comments section is powered by <a href="http://modxcms.com/extras/package/538">Quip</a>, a commenting solution I wrote for MODx Revolution. Some of you have asked how I got reCaptcha support working with it. Well, to be honest, reCaptcha support is built-in to Quip.</p>

<p>First off, Quip requires 2 calls - one for displaying the comments for a thread:</p>

<pre class="brush: xhtml">
[[!Quip?
  &thread=`blog-post-[[*id]]`
  &replyResourceId=`19`
]]
</pre>

<p>This call in my 'BlogTemplate' template tells me to grab all comments within the thread for the current Resource. There's also a 'replyResourceId' value which is just an ID of a Resource that has just a Quip call in it (it's for replying to threaded posts). Then, there's a Quip call for displaying the reply form:</p>

<pre class="brush: xhtml;">
[[!QuipReply?
   &thread=`blog-post-[[*id]]`
   &recaptcha=`1`
   &notifyEmails=`-emailremoved-`
]]
</pre>

<p>This call tells Quip to display the Reply form for the specified thread, and notify me by email when a reply is posted. Note all I did to enable reCaptcha support is pass in a parameter called 'recaptcha' and set it to 1. Simple as that. Quip handles the rest.</p>

<p>The only other thing I had to do was set a few System Settings that had to do with my public and private reCaptcha API keys:</p>

<ul>
<li>recaptcha.private_key</li>
<li>recaptcha.public_key</li>
</ul>

<p>And then I set 'recaptcha.use_ssl' to 'Yes' for extra security.</p>