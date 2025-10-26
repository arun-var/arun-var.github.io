---
layout: page
title: Life & Notes
subtitle: Short ideas, drafts, and links.
permalink: /notes/
---

<ul class="post-list">
{% assign cat = 'notes' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

