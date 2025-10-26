---
layout: page
title: Investing
subtitle: ETF cores, risk rules, and pragmatic strategy.
permalink: /investing/
---

<p>Evidence-based ideas you can stick with.</p>

<ul class="post-list">
{% assign cat = 'investing' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

