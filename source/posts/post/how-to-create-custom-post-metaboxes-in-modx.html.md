---
title: How to Create Custom Post Meta Boxes in MODX
date: 2011-10-04 23:01 CDT
tags: modx, wordpress
teaser: A simple little comparison tutorial on creating custom fields in MODX as opposed to WordPress.
---

## What is a Meta Box?

In the article, they talk about "Meta boxes", which they explain as such:

  Its purpose is to allow the user to select or enter information in addition to the main post content.

Sounds handy. Does MODX have that? Why, yes, it does. In fact, it has it in the core.

### What is a Template Variable?

A Template Variable - or TV - in MODX is simply a custom field for your Resource (in WordPress they call it a Page). You assign it to any Templates - which are "containers" for your pages - you want. Want a custom field of "tags" and have a Blog Template, a News Template, and a Contact Template? Want that "tags" field on all of them? Simple as cake in MODX. And that's no lie.

To start, all you do in MODX to create a TV is click on the New TV option here:

<img src="https://img.skitch.com/20111005-kt1tjepai58s6d1qt49h7gnnnr.jpg" alt=" " width="311" height="367" />

And then simply name it whatever you want. We'll name ours "MyTV":

<img src="https://img.skitch.com/20111005-tb82am5156f77puuayjpgm94x5.jpg" alt=" " width="567" height="319" />

You can add a description as well, and even adjust the "Input Options" (or how it renders in the backend, such as a textbox, textarea, dropdown, tag field, checkbox, etc) and "Output Options" (regular text, img tag, URL, etc) for it as well. Then assign it to whatever Templates you want, and viola! You have a custom field:</p>

<img src="https://img.skitch.com/20111005-edke7be8brwr53u77f41maj7yy.jpg" alt=" " width="601" height="362" /></p>

Oh, and by the way - you could move this TV out of the Template Variables tab and into any other tab, if you wanted, making it a "first-class citizen" in the content. There's a nifty UI in MODX, called "[Form Customization](http://rtfm.modx.com/display/revolution20/Customizing+the+Manager)", to do that in. And your custom field is reference-able in your page with the nice little tag: &#91;&#91;*MyTV&#93;&#93;. No PHP code necessary at all.

### In Summary

So, yes, in less than one minute you can create a custom field in MODX. I mean, if you want to go <a href="http://wp.smashingmagazine.com/2011/10/04/create-custom-post-meta-boxes-wordpress/">the WordPress route</a>, you can, but I think I'll take the easy road...

#### Late Update
Some have argued that WP's Post Meta is attributed to Post Types, which are more like Resource Types rather than Template-related Variables. My argument is that is moot - when is a presentation of a Resource and its content not linked? The nomenclature may differ, but MODX's architecture of custom fields is more flexible and powerful according to the way that content is presented.