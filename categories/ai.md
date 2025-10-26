---
layout: page
title: AI & Automation
subtitle: Practical prompts, agents, and workflow automation.
permalink: /ai/
---

<p>Playbooks and tooling to actually ship AI features and automations.</p>

<ul class="post-list">
{% assign cat = 'ai' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

