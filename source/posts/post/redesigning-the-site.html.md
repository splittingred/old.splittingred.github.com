---
title: Redesigning the Site
date: 2013-06-19 10:18 CDT
tags: middleman, ruby, markdown
teaser: Well, I did it. I finally decided to redo my site. Not only did I move to a new design, I went a few steps further.
---

Well, I did it. I finally decided to redo my site. Not only did I move to a new design, I went a few steps further.

## Going Static

I've fully moved off of [MODX](http://modx.com/), as it was a bit too much for the tiny site that this was. I love MODX,
and would still highly recommend it to people building larger or mid-grade sites; however for my small little blog, I
wanted something I could quickly deploy up and get adding content to fast.

## Enter MiddleMan

I've been doing a lot of Ruby coding recently, and decided, why not make my blog out of it? After toying around with
[Jekyll](http://jekyllrb.com/) for a while, I eventually settled on [MiddleMan](http://middlemanapp.com/), an easy build
and deploy tool that I could throw a site up quickly via a Git repository.

I redesigned the site with a very, very simple and minimalistic design (still a WIP, of course). I wanted content to be
king on the site, and didn't want to have to think about design trends over the next few years. Choosing the plain
design enabled me to concentrate more on *what* I want to write, rather than how it is going to look.

## Formatting

I also wanted to be able to type posts fast, without having to worry about markup. Enter [Markdown](http://daringfireball.net/projects/markdown/),
which I've been using for years in wikis and readmes, but haven't full-out blogged with it yet. MiddleMan has a nice
integration with Markdown, and all my blog posts are now just simple Markdown syntax.

## Deploying

Deploying in MiddleMan is absurdly simple. Once I've got my post the way I want it, previewable via MiddleMan's dev
server, I just load up terminal and type "middleman build". It automatically builds the site down to a static page, and
then throws it up into my [GitHub repository](https://github.com/splittingred/splittingred.github.com).

For now, I'm still hosting on my server, but I may move to take advantage of GitHub's Pages for hosting. Currently
on my server I have a simple cronjob that updates the local git repo every minute, keeping my site running with some
nice continuous integration steps. One-step push to deploy. Gotta love it.