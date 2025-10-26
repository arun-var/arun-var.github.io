---
layout: page
title: Football
subtitle: Tactics, analysis, and notebook-style breakdowns.
permalink: /football/
---

<p>Compact explainers and match notes.</p>

<ul class="post-list">
{% assign cat = 'football' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

