---
title: Tagging Blog Posts in Revolution
date: 2010-05-04 13:42 CDT
tags: modx, tagging, taxonomy
teaser: So, you might ask, how did I do the tagging in this blog? In this post, I'll show some of the snippets and code that got the sleek tagging on splittingred.com.
---


**Note: Since I wrote this, I've released <a href="http://modxcms.com/extras/package/691" target="_blank">tagLister 1.0.0-pl</a>, which actually has both 'tolinks' and 'getResourcesTag' packaged in with it, so you wont need to manually add these snippets - just download the tagLister Extra.**

This is basically how I setup tagging for this blog; I dont purport to state that this is the *only* way to do tagging. I know for a fact <a href="http://jasoncoward.com/">Jason</a> does his tagging differently. However, for those interested, I thought I'd post my method.

<p>To do tagging in Revo using this approach, you'll need to have downloaded the following snippets: "getPage" and "getResources". These snippets are vital for any blog, for that matter.</p>

<h4>Creating the Tags TV</h4>

<p>First off, you'll need to create a TV called 'tags', and assign it to your blog post template. (Assuming you have a separate template for blog posts.) Make it a textfield, with no output widgets or renders.</p>

<h4>Adding the Tags to Your Chunk</h4>

<p>Now, find your 'blogPost' chunk, or whatever chunk you are using to iterate a list of posts using getResources. Put this line wherever you want the tags to show up:

<pre class="brush: html">
[[+tv.tags:notempty=`<span class="tags">Tags: [[!tolinks? &items=`[[+tv.tags]]` &key=`tag`]]</span>`]]
</pre>

<p>Okay, a few things here. One, the +tv.tags placeholder represents in getResources your TV called 'tags' which we created earlier. Next, you'll notice that we only show the 'tags' span if tags actually has content. Third, we have a snippet we're running called 'tolinks'. This snippet makes tags out of the links.</p>

<h4>Creating the tolinks Snippet</h4>

<p>Go ahead and create the snippet called 'tolinks' and paste this code in:</p>

<pre class="brush: php">
/**
 * Creates links out of tags
 */
$inputDelim = $modx->getOption('inputDelim',$scriptProperties,',');
$outputDelim = $modx->getOption('outputDelim',$scriptProperties,', ');
$key = $modx->getOption('key',$scriptProperties,'tag');
$target = $modx->getOption('target',$scriptProperties,$modx->resource->get('id'));

$items = explode($inputDelim,$items);
$tags = array();
foreach ($items as $item) {
    $item = trim($item);
    $url = $modx->makeUrl($target,'','?'.$key.'='.$item);
    $url = str_replace(' ','+',$url);
    $tags[] = '<a href="'.$url.'">'.$item.'</a>';
}

return trim(implode($outputDelim,$tags),$outputDelim);
</pre>

<p>Basically, this code takes an input and splits it by a delimiter, makes links from it, and then outputs it back, separated by an output delimiter. So, in our tags instance, it will take in any tags the poster puts into the 'tags' TV, split them by commas, and then post them back out with link tags added.</p>

<p>It also allows you to specify *where* that URL goes to, via the 'target' property. Since I want to point it to my home page (resource ID 1), I'll pass 1 as the 'target' property. However, if you want it to point somewhere else, either change the default value or pass that Resource ID as a 'target' parameter into the 'tolinks' snippet call.</p>

<p>We're almost done! Now we're just going to add a wrapper snippet around getPage and getResources.</p>

<h4>Adding the getResourcesTag Wrapper Snippet</h4>

<p>Okay, so we've got our system showing the contents of our TV in clickable tag format. But we want stuff to actually *happen* when we click on those tags. We want getResources to filter by the tags we specified. So, we're going to create a 'wrapper' snippet that handles this for us.</p>

<p>Go ahead and make a snippet called 'getResourcesTag' and paste the following into it:</p>

<pre class="brush: php;">
/**
 * Wrap the getPage/getResources call to implement tagging
 */
if (!empty($_GET['tag'])) {
    $scriptProperties['tvFilters'] = 'tags==%'.$_GET['tag'].'%';
}
$elementObj = $modx->getObject('modSnippet', array('name' => 'getPage'));
if ($elementObj) {
    $elementObj->setCacheable(false);
    $output = $elementObj->process($scriptProperties);
}
return $output;
</pre>

<p>Note that all this does is pre-set the 'tvFilters' property for getPage (which wraps getResources) with the REQUEST variable 'tag'.</p>

<p>So, in our Resource that we want to display a list of blog posts, assuming we've <a href="[[~15]]">set the blog up in a good structure</a>, we can do the following getResourcesTag call:</p>

<pre class="brush: html">
[[!getResourcesTag?
  &parents=`8,9`
  &hideContainers=`1`
  &depth=`2`
  &includeTVs=`1`
  &tpl=`blogPost`
  &elementClass=`modSnippet`
  &element=`getResources`
  &pageVarKey=`page`
]]
[[!+page.nav:notempty=`
<div class="paging">
<ul class="pageList">
  [[!+page.nav]]
</ul>
</div>
]]
</pre>

<p>You can put the properties on the getResourcesTag call in a Property Set as well, to make it so you can call this snippet from anywhere on your site.</p>

<p>And we're done! Instant tagging for our blog:</p>

<img src="http://splittingred.s3.amazonaws.com/blog/old/tagging-tv.png" alt="the tags tv" />