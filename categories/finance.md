---
layout: page
title: Personal Finance & Investing
subtitle: Canada-focused money basics, ETF cores, and pragmatic risk rules.
permalink: /finance/
redirect_from:
  - /personal-finance/
  - /investing/
---

<p>Evidence-based money and investing ideas you can actually stick with.</p>

{% comment %} Merge the old 'personal-finance' and 'investing' categories into one list {% endcomment %}
{% assign finance = '' | split: '' %}
{% if site.categories['personal-finance'] %}{% assign finance = finance | concat: site.categories['personal-finance'] %}{% endif %}
{% if site.categories['investing'] %}{% assign finance = finance | concat: site.categories['investing'] %}{% endif %}
{% if site.categories['finance'] %}{% assign finance = finance | concat: site.categories['finance'] %}{% endif %}
{% assign finance = finance | uniq | sort: 'date' | reverse %}

<ul class="post-list">
{% for post in finance %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

{% if finance.size == 0 %}
<p>No posts here yet — coming soon.</p>
{% endif %}
