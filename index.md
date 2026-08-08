---
layout: page
title: AV
subtitle: Build systems. Invest wisely. Live better.
# Good for SEO/social
description: "DevOps & Cloud engineer writing playbooks on AWS, Kubernetes, CI/CD, AI, personal finance, and investing."
image: /assets/img/og-default.jpg
---

<!-- HERO -->
<section class="hero container">
  <h1>DevOps & Cloud engineer helping companies ship faster and safer</h1>
  <p>I'm {{ site.author }} — building resilient systems, automating work, and investing wisely.</p>
  <a class="btn btn-primary" href="/atom.xml">Subscribe</a>
</section>

<!-- WHAT I DO (CONSULTING) -->
## What I Do
- **DevOps & CI/CD**: GitHub Actions, Jenkins, GitLab CI
- **Cloud Infrastructure**: Scalable AWS architectures & cost controls
- **Kubernetes**: EKS/ECS, service mesh
- **SRE**: Observability, incident response, on-call ergonomics

<div>
  <a class="btn btn-primary" href="/services/">View Services</a>
  {% if site.projects.size > 0 %}
  <a class="btn" href="/projects/">See Projects</a>
  {% endif %}
</div>

---

<!-- TOPIC CARDS -->
<section class="topics container">
  <h2>Topics</h2>
  <div class="cards">
    <a class="card" href="/ai/">
      <h3>AI & Automation</h3><p>Prompts, agents, workflows.</p>
    </a>
    <a class="card" href="/tech/">
      <h3>Technology & Engineering</h3><p>AWS, Kubernetes, Terraform.</p>
    </a>
    <a class="card" href="/finance/">
      <h3>Personal Finance & Investing</h3><p>Canada-focused money, ETFs, and risk.</p>
    </a>
    <a class="card" href="/misc/">
      <h3>Miscellaneous</h3><p>Notes, ideas, and everything else.</p>
    </a>
  </div>
</section>

---

<!-- FEATURED POSTS (tag pillar posts with `featured`) -->
{% assign featured = site.tags.featured %}
{% if featured and featured.size > 0 %}
## Featured Guides
<ul>
  {% for post in featured limit:6 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
{% endif %}

<!-- LATEST POSTS -->
## Recent Posts
<ul>
  {% for post in site.posts limit:8 %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="date"> — {{ post.date | date: "%b %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>

<div>
  <a class="btn" href="/blog/">View all posts</a>
  <a class="btn" href="/atom.xml">RSS</a>
</div>

<!-- PRIVACY: no tracking, by design -->
<p class="privacy-note">
  🔒 <strong>No cookies. No trackers. No ads.</strong>
  This site doesn't run analytics or set cookies — your visit isn't logged, profiled, or sold.
  <a href="/privacy/">How this works →</a>
</p>
