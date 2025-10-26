---
layout: page
title: Arun Varghese
subtitle: DevOps & Cloud engineer helping startups ship faster and safer
---

Hi! I'm Arun, a DevOps and Cloud engineer specializing in AWS, Kubernetes, and CI/CD pipelines.

I help teams ship faster, safer, and more cost-effectively through infrastructure automation, reliability engineering, and cloud architecture.

## What I Do

- **DevOps & CI/CD**: Build robust pipelines with GitHub Actions, Jenkins, and GitLab CI
- **Cloud Infrastructure**: Design and implement scalable AWS and cloud solutions
- **Kubernetes**: Container orchestration, EKS/ECS deployments, and service mesh
- **Site Reliability Engineering**: Observability, incident response, and on-call optimization

## Work With Me

I offer freelance consulting services including DevOps acceleration, cloud readiness audits, and SRE hardening.

[View Services](/services/){: .btn .btn-primary} [See Projects](/projects/){: .btn}

## Recent Posts

Check out my latest thoughts on DevOps and cloud engineering:

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url | relative_url }}) - {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}

[View all posts](/blog/){: .btn}
