---
title: Why I Can't Respond Privately (MODX)
date: 2010-10-25 14:39 CDT
tags: modx, agile, community
teaser: Overheard "The MODx team doesn't care." "There's no support." "They never got back to me!" "My site is failing because of X bug and the developer isn't responding. My client's going to kill me!" "MODx isn't stable." "This product is going to fail."
---

I hear these statements daily. Via forum posts, Twitter, personal messages, email, facebook, you name it. (<strong>Important Disclaimer</strong>: The number of positive responses vastly dwarfs negative ones.) What do I do about it?

Well, first, like any problem, it's important to diagnose <em>why</em> someone feels something, before addressing the problem itself. The scenario is this: You've just adopted MODx Revolution - a hot, brand-new product that the <a href="http://www.cmscritic.com/modx-revolution-2-0-review/">web community</a> <a href="http://codingpad.maryspad.com/2010/08/18/modx-revolution-for-beginners-part-1-introduction/">is</a> <a href="http://ichosemodx.wordpress.com/2010/02/04/why-i-chose-modx-over-drupal-part-one/">buzzing</a> <a href="http://www.cmswire.com/cms/web-cms/web-cms-modx-revolution-targets-drupal-joomla-markets-008104.php">about</a>. You've downloaded it, installed it, and signed up a client to use it.

All's well in the world, right? Well, no - you've hit a snag with either your implementation, a bug somewhere, or you just aren't sure how to do X. And you're stumped. You've read <a href="http://rtfm.modx.com">the manuals</a> (I may be being generous here in that assumption), but still don't get it. And you're not a coder, most likely, so looking at the code is out of the question.

Not knowing what to do, you start asking anyone and everyone for help. You post in the forums, but no one (sufficiently) responds. Or if they do, it doesn't fully solve your problem. So what do you do now? Well, here's where we go awry. You email or contact the developer (in this case, me) via email, IRC or PM and ask for help. And you expect them to answer, right? Or at least answer the email.

<hr />

Okay, we've setup our scenario. Now let me go ahead and say it - _this is completely understandable_. Sometimes things don't work as expected, or aren't fully documented. Bugs happen. Any developer understands that, and they are trying their best to minimize problems. But to be fair, let's do a scenario from their perspective:

You just spent 2 days of unpaid time to contribute an Extra to MODx. You've poured over the code, tested it, got it running, and submitted it to modxcms.com. It's been approved, and then reality sets in. People are going to be using your product. You scramble to write out some documentation, and try to write it to the best of your ability - but you're no technical writer. You hope that someone else will come in and clean it up.

In fact, you're hopeful that all you read about this "Open Source" movement stuff that people write about in blogs will *actually happen*. You've read that people (called "givers") actually contribute back code when they find bugs. They write how-tos and tutorials. Some will even donate! Giddy and optimistic, you're thrilled that your Extra is up and ready for use, and you tell everyone about it. Giving free software is great!</p>

<p>But then reality hits. About 2% of your users actually give back (and you're eternally thankful, more than even they realize). The rest passively, silently use your product without any amount of thanks, support or contribution. They click and disappear. But you know, that isn't that bad. You can deal with people just being happy. They'll submit bugs if they hit them. Right?</p>

<p>Well, statistically speaking, no. To be honest though, that's okay. You can deal with that. But then come the "consumers". This is what you call them, because in your mind as a developer, that's what they do. They consume the product, the code, the documentation, you. They give nothing back but questions on why something doesn't work. Why the documentation is hard to read. Why there's bugs in the first place. How they're entitled to their say and you should be fixing their product. Then they start <em>emailing you directly</em>, asking for help. Swamped with this, it's easy to see why you're quickly losing motivation (and time) to code anything new. Why invite more criticism? After all, you're not getting paid for this.</p>

<hr />

<p>Obviously, this is a bit anecdotal. This doesn't always happen to this extent, or even in this order. It's never this black and white. But I do see it every day - with myself, my colleagues, and those who contribute. How do we solve this problem?</p>

<p>I think the problem and the answer is the same: <strong>community</strong>. So much of how community behaves is defined by that community itself, and the action principal members of that community take.</p>

<p>Personally, I do not respond to individual support requests or personal messages (with a few rare exceptions). Why, you ask? Wouldn't that help develop community? Doesn't ignoring it hurt the product? Well, actually, the truth might be startling: <strong>no</strong>. Not at all. Let's look at a graph:</p>

<img src="http://splittingred.s3.amazonaws.com/blog/old/graph-resp-1.png" alt="" />

<p>This graph shows a hypothetical (and somewhat realistic) scenario in which I decide to take in support requests. A low estimate of the number of emails/PMs I get a day is 2 new ones per day (it's more like 3-5). I also assume (again, a low estimate) that each response takes 30 minutes of work. This scenario assumes that I respond - and we also assume that <em>persists</em> the communication and support, since I'd have to respond to their response, and so forth. So the first day, I've got one request. 30 minutes gone from my development time that day. Not bad. But see what happens to my free time as I add more responses? The amount of time I get to actually <em>fixing</em> the product decreases exponentially. By Day 5 I'm barely even coding or documenting anymore.</p>

<p>This is why I don't respond to personal requests. I leave it up to the community to support itself, with some help from me when I can. I believe this promotes a healthier community - one that learns, grows and helps each other, rather than leaning heavily on the core team or experts within the community. It discourages dependence and encourages communal growth and independence.</p>

<p>I recommend people post in the forums, where others besides myself can come in and help. (And for non-coders, that's actually a huge contribution that they can do.) Forums also have the side benefit of being searchable and archivable, meaning questions don't always have to be re-asked. I contribute much more effectively to support by:</p>

- Writing more documentation
- Fixing said bugs
- Developing the product more
- Getting developers who want to contribute back docs/help on how to do so
</ul>

<p>These measures are <strong>far</strong> more effective at product and community development than me responding to everyone's problems. This is also how I'm sure many other developers look at it. We're not ignoring you. We're just helping more effectively. Please don't take it personally - we really do love you. That's why we spend all this time giving you this for free.</p>

<p>All that said, the mantra we must remember in Open Source is that "you get what you give". OSS lives and dies by that saying. So with that said, let's be a community of "givers" rather than "consumers".</p>

<hr />

<p>PostScript: Obviously, I respond to people with security vulnerabilities found, or potential developers. I'm also <strong>far</strong> more likely to respond to bugs filed in the <a href="http://bugs.modx.com/">MODx bugtracker</a>. Nothing's black and white, and I'm constantly evaluating the merit and value of any situation. But this is a general guide to how I decide on how to spend my time.</p>