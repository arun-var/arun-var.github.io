---
layout: page
title: Tags
permalink: /tags/
---

{% assign tags = site.tags | sort %}
{% for tag in tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<h2 id="{{ t | downcase | replace: ' ', '-' }}">{{ t }}</h2>
<ul>
  {% for post in posts %}
    {% if post.tags contains t %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="text-muted">{{ post.date | date: "%B %-d, %Y" }}</span>
    </li>
    {% endif %}
  {% endfor %}
</ul>
{% endfor %}
