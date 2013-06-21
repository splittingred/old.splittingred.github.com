---
title: A New Extras Section
date: 2011-02-17 16:43 CDT
tags: modx, extras
teaser: Okay, so it's been a bit quiet at MODX since the new modx.com site launch. We've been busy. Very busy. Personally, I've been working on a complete rewrite of the Extras section for MODX. Read on for a sneak peek.
---

<p>The old site's Extras section was a massive undertaking - we wanted a scalable solution, but had little time to develop it. So we threw something together, and integrated it into MODX Revolution so that you could download straight from the website to your Revo instance. It was pretty neat at the time, but there were some definite drawbacks. The search stunk. Loading wasn't nearly as fast as we'd have liked it to be. The star rating system was, well, meh. It wasn't exactly pretty, either.</p>

<p>So, after the new site launch, we've decided to spend some time working on it. In fact, that's about all I've been doing for the past 2 weeks. And boy, am I excited about it. We wanted the following to happen:</p>

<ul>
<li>Styled and fit into the design of the new <a href="http://modx.com">modx.com</a>.</li>
<li>A much more powerful, easy to navigate search.</li>
<li>Some kind of flag for "Featured" and "Solid" Extras, which are Extras being featured or audited as solid packages by the core team.</li>
<li>Weighted search results so we can promote certain Extras if needed.</li>
<li>A much easier submission process. The current one is confusing, and not easy to do.</li>
<li>Integration into our modx.com SSO-driven backend system, so we can do all kinds of fun things with the data (like upcoming awards/badges/xp etc).</li>
<li>Get rid of the star rating system and move to a simpler like/unlike system.</li>
<li>Better stats!</li>
</ul>

<p>First off, here's a sneak peek of the new browsing view, where you can browse
categories and search from:</p>

<a href="http://splittingred.s3.amazonaws.com/blog/old/extras-browse.351d13229ee149015ce475fb9dd0b4d156.png" rel="prettyPhoto[gal]"><img src="http://splittingred.s3.amazonaws.com/blog/old/extras-browse.351d13229ee149015ce475fb9dd0b4d156.png" /></a>

<p>Obviously, it's a bit rough, but we're ironing out the issues now. As you can see, we've added direct download links straight on the search page - no longer do you need to drill in to download an Extra. Also, we've fixed the search so that searching for "If" now returns the If Extra on the first result, and pagination actually shows the correct number of results. Joy!</p>

<p>If you do decide to drill down, however, you'll get something like this view:</p>

<a href="http://splittingred.s3.amazonaws.com/blog/old/extras-details.351d13229ee149015ce475fb9dd0b4d156.png" rel="prettyPhoto[gal]"><img src="http://splittingred.s3.amazonaws.com/blog/old/extras-details.351d13229ee149015ce475fb9dd0b4d156.png" /></a>

<p>One big, clear button for your Downloads. This does mean we'll be restricting Extras to one file for downloads, but trust us - this will make the whole process much simpler. We've also added Like and Tweet buttons, a more coherent tabbed interface (built on jQuery tabs), and a new feature: "Changelog". Here you can put the latest changes to your Extra's Version. This will make it much easier for people to see what's new on your Extra.</p>

<p>Not to mention a nice gallery view for your screenshots:</p>

<a href="http://splittingred.s3.amazonaws.com/blog/old/extras-ss.351d13229ee149015ce475fb9dd0b4d156.png" rel="prettyPhoto[gal]"><img src="http://splittingred.s3.amazonaws.com/blog/old/extras-ss.351d13229ee149015ce475fb9dd0b4d156.png" /></a>

<p>And of course, the previous versions view and screenshots for your Extra will still be around. You'll be able to mark Versions as 'active' or 'inactive' now, so if you need to quickly take a Version down temporarily, you'll be able to do so.</p>

<p>Also, we're adding a "Deprecate Prior Versions" option that is checked by default on your Submit New Version page, which will automatically deprecate all your prior versions for that Extra after your new Version is approved. This will be extremely useful, as deprecated versions dont show in search results, and will keep your listings nice and clean.</p>

<p>We've also improved the speed big time (the DB model is now using rails/mongodb/solr connected to via the built-in REST services in Revolution - it's pretty fancy.). You'll see pages load way-fast, and be a ton more scalable as MODX contributions grow.</p>

<p>Finally, this will all integrate into your modx.com account. You'll be able to see the Extras you've submitted, and all of this will count toward your account. We'll be introducing even more cool stuff on modx.com as the year progresses - and let's just say contributions (including Extras, rtfm docs edits, downloads, forum posts, showcase site submissions, job listings, help wanted ads, donations, etc) will have a "measurable quality" soon enough. ;)</p>

<p>Oh, and we're still developing the next branch for Revolution, 2.1. We've already <a href="https://github.com/modxcms/revolution/commit/d964b98cad2ffe99f9344c39e62706ce08b787cb">vastly improved the caching system</a>, and added TV Input Options which allow you to restrict or require input values to TVs, and add a slew of <a href="https://img.skitch.com/20110120-kmqf8raa6e1ag53fytuyjb7115.jpg">new options</a> to them (another blog post on that later). If you're not a <a href="http://modx.com/partners/">MODX Partner</a> yet, let's just say there's lots of incentives coming down the pipes. Thanks!</p>