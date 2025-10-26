---
layout: page
title: Technology & Engineering
subtitle: AWS, Kubernetes, Terraform, CI/CD, and SRE notes from the field.
permalink: /tech/
---

<p>Real-world infra, pipelines, reliability, and cost control.</p>

<ul class="post-list">
{% assign cat = 'tech' %}
{% for post in site.categories[cat] %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
  </li>
{% endfor %}
</ul>

