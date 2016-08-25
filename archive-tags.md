---
layout: page
title: Blog Archive
permalink: /archive/tags
banner_image: archive-banner.jpg
---
<div>
<a href="{{site.url | append: site.baseurl}}/archive/chron">View by dates</a>
</div>

### Tags
<div>
{% assign sortedtags = site.tags | sort %}
{% for tag in sortedtags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <a name="{{t | slugify}}"></a><h4>{{t}}</h4>

  <ul>
  {% for post in posts %}
    {% if post.tags contains t %}
      <li>
        <a href="{{ post.url | append: '/' | replace: '//', '/' | prepend: site.baseurl | prepend: site.url |  }}">{{ post.title }}</a>
        <span class="archive-meta"> - {{ post.tags | join: ", " }} - {{ post.date | date: "%B %-d, %Y"  }}</span>
      </li>
    {% endif %}
  {% endfor %}
  </ul>
{% endfor %}
</div>
