---
layout: page
title: Personal Finance (Canada)
subtitle: Simple rules for cashflow, credit, TFSA/RRSP, and taxes.
permalink: /personal-finance/
---

<p>Canada-focused basics that actually move the needle.</p>

<ul class="post-list">
{% assign cat = 'personal-finance' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

