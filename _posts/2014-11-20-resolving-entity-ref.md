---
layout: post
categories: blog
tags: [data science, coding, scraping, munging, XML]
title: Resolving EntityRef - Expecting ';'
preview_pic: /assets/images/2014-11-20-resolving-entity-ref.png
comments: true
---

So [Frank](http://frankchen07.github.io) and I were scraping data off the web (with permission, of course) using R's `XML` package when suddenly a wild error appeared!

```
doc <- "http://somesite.com/xml.php?Y2=2005&max=100"
xmlParse(doc)
```

`Error: EntityRef: expecting ';'`


A quick search brought up a [few](http://stackoverflow.com/questions/23422316/xml-validation-error-entityref-expecting) [StackOverflow](http://stackoverflow.com/questions/3431280/validation-failed-entityref-expecting) [posts](http://stackoverflow.com/questions/19696797/read-xml-file-using-lxml-get-error-entityref) and [blogs](http://mrrena.blogspot.com/2009/07/entityref-expecting-at-line-1.html) offering common solutions. At first glance, we thought that the URL query string was the culprit of our woes - the `xmlParse()`` function could not read the unescaped ampersands!

However, whether we passed the URL without the escaped ampersands:

`"somesite.com/results_xml.php?Y2=2005**&**max=100"`

or with the escaped ampersands:

`"somesite.com/results_xml.php?Y2=2005**&amp;**max=100"`

we still received the same exact error:

`Error: EntityRef: expecting ';'`

On the verge of nearly pulling our hairs out, we decided to examine the XML data more thoroughly. Only then did we find our problem child:

<figure>
<img src = "/assets/images/2014-11-20-resolving-entity-ref.png" class = "halfw"></img>
</figure>

![Never thought I'd say this, but M&M's just left a bad taste in my mouth.]()

There were unescaped ampersands in the XML file itself! These sneaky guys were throwing the "EntityRef" error in the `xmlParse()` function all along. With this in mind, we tweak our approach to replace all unescaped ampersands in the XML file with the appropriate encoding:

<figure>
<script src="https://gist.github.com/rcquan/79362081c0ff960c4da6.js"></script>
</figure>

So lesson learned: always check to see if you have a valid XML file before attempting to parse the data using any sort of scraper.

