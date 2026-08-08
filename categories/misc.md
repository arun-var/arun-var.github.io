---
layout: page
title: Miscellaneous
subtitle: Everything else — notes, ideas, and the occasional rabbit hole.
permalink: /misc/
---

<p>Assorted posts that don't fit the other topics.</p>

<ul class="post-list">
{% assign cat = 'misc' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

{% if site.categories[cat].size == 0 %}
<p>No posts here yet — coming soon.</p>
{% endif %}
