---
layout: page
title: Blog Archive
permalink: /archive/tags
banner_image: archive-banner.jpg
---
<a href="/archive/chron">Sort chronological</a>

### Categories
<div>
{% assign sortedtags = site.tags | sort %}
{% for tag in sortedtags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <!-- only use tag as category if it's used in some post as first tag -->
  {% for post in posts %}
    {% if post.tags[0] == t %}
      <h4>{{ t | downcase }}</h4>
      {% break %}
    {% endif %}
  {% endfor %}

  <ul>
  {% for post in posts %}
    {% if post.tags[0] == t %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span class="archive-meta"> - {{ post.date | date: "%B %-d, %Y"  }}</span>
      </li>
    {% endif %}
  {% endfor %}
  </ul>
{% endfor %}
</div>
