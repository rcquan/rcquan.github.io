---
layout: page
title: Archive
permalink: /archive/
---

<p class="lede">From my earlier blogging days (2013&ndash;2015): public health, data science, and a lot of curiosity. Some of it is dated, but I'm keeping it up.</p>

{% assign years = "2015,2014,2013" | split: "," %}
{% for year in years %}
<h2>{{ year }}</h2>
<ul class="archive-list">
  {% for post in site.posts %}
    {% assign post_year = post.date | date: "%Y" %}
    {% if post_year == year %}
    <li><span class="post-meta">{{ post.date | date: "%d %b" }}</span> <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
{% endfor %}
