---
layout: page
title: Freelance Services
subtitle: I help teams ship faster, safer, and cheaper with AWS, Kubernetes, and CI/CD
permalink: /services/
---

{% for item in site.data.services %}

## {{ item.title }}

{{ item.description }}

**Deliverables:**

{% for deliverable in item.deliverables %}
- {{ deliverable }}
{% endfor %}

[{{ item.cta.label }}]({{ item.cta.url }}){: .btn .btn-primary}

---

{% endfor %}

## Get Started

Ready to improve your infrastructure and deployment processes? [Contact me](/contact/) to discuss your project.
