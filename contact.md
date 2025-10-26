---
layout: page
title: Contact
subtitle: Tell me a bit about your context and goals.
permalink: /contact/
---

<section class="container">
  <p>If you’re exploring an engagement or want a second set of eyes on your infra, send a short note below. I typically reply within 1–2 business days.</p>

  <form class="contact-form" action="https://formspree.io/f/your-id" method="POST">
    <!-- Anti-bot honeypot -->
    <input type="text" name="_gotcha" style="display:none">

    <div class="form-row">
      <label for="name">Name</label>
      <input id="name" name="name" type="text" required>
    </div>

    <div class="form-row">
      <label for="email">Work email</label>
      <input id="email" name="email" type="email" required>
    </div>

    <div class="form-row">
      <label for="company">Company (optional)</label>
      <input id="company" name="company" type="text">
    </div>

    <div class="form-row">
      <label for="topic">Topic</label>
      <select id="topic" name="topic" required>
        <option value="">Choose one</option>
        <option>DevOps & CI/CD</option>
        <option>Cloud Architecture (AWS)</option>
        <option>Kubernetes</option>
        <option>SRE & Observability</option>
        <option>Cost & Reliability Review</option>
        <option>AI & Automation</option>
        <option>Other</option>
      </select>
    </div>

    <div class="form-row">
      <label for="budget">Rough budget (optional)</label>
      <select id="budget" name="budget">
        <option value="">Not sure yet</option>
        <option>Under $5k</option>
        <option>$5k–$15k</option>
        <option>$15k–$40k</option>
        <option>$40k+</option>
      </select>
    </div>

    <div class="form-row">
      <label for="message">What’s the goal? What’s in the way?</label>
      <textarea id="message" name="message" rows="6" required></textarea>
    </div>

    <button class="btn btn-primary" type="submit">Send</button>
  </form>

  <div class="contact-alt">
    <p><strong>Prefer email?</strong> {{ site.email }}</p>
  </div>
</section>
