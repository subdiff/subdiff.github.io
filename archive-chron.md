---
layout: page
title: Blog Archive
permalink: /archive/chron
banner_image: archive-banner.jpg
---
<div>
<a href="{{site.url | append: site.baseurl}}/archive/tags">View by topics</a>
</div>

### Chronological
<div>
  <ul>
    {% assign sortedposts = site.posts %}
    {% for post in sortedposts %}
      {% capture currentyear %}{{post.date | date: "%Y"}}{% endcapture %}
      {% if currentyear != year %}
        <h4>{{ currentyear }}</h4>
        {% capture year %}{{currentyear}}{% endcapture %} 
      {% endif %}
      <li>
        <a href="{{ post.url | append: '/' | replace: '//', '/' | prepend: site.baseurl | prepend: site.url |  }}">{{ post.title }}</a> <span class="archive-meta"> - {{ post.tags | join: ", " }} - {{ post.date | date: "%B %-d, %Y"  }}</span>
      </li>
    {% endfor %}
  </ul>
</div>
