---
layout: page
title: Certificates
permalink: /certificates/
description: Courses I have completed, newest first.
nav: true
nav_order: 2
---

<div class="cert-list">
  {% for cert in site.data.certificates %}
    <article class="cert-card">
      <div class="cert-card-image">
        {% assign cert_base = cert.image | remove: '.jpg' | remove: '.jpeg' | remove: '.png' %}
        <img
          src="{{ cert.image | relative_url }}"
          {% if site.imagemagick.enabled %}
            srcset="{% for width in site.imagemagick.widths %}{{ cert_base | relative_url }}-{{ width }}.webp {{ width }}w{% unless forloop.last %}, {% endunless %}{% endfor %}"
            sizes="(min-width: 768px) 420px, 90vw"
          {% endif %}
          data-zoom-src="{{ cert.image | relative_url }}"
          data-zoomable
          loading="lazy"
          width="1600"
          height="1200"
          alt="{{ cert.title }} certificate from {{ cert.issuer }}"
        >
      </div>
      <div class="cert-card-body">
        <p class="cert-issuer">
          {% if cert.issuer_icon %}<i class="{{ cert.issuer_icon }}" aria-hidden="true"></i>{% endif %}
          {{ cert.issuer }}
        </p>
        <h2 class="cert-title">{{ cert.title }}</h2>
        <p class="cert-date">Issued {{ cert.date | date: '%B %-d, %Y' }}</p>
        {% if cert.credential_id %}
          <p class="cert-id">Credential ID <code>{{ cert.credential_id }}</code></p>
        {% endif %}
        {% if cert.url %}
          <a class="pill-button" href="{{ cert.url }}">Verify certificate <i class="fa-solid fa-arrow-up-right-from-square" aria-hidden="true"></i></a>
        {% endif %}
      </div>
    </article>
  {% endfor %}
</div>

<p class="page-note">More to come as I keep learning. <span aria-hidden="true">📚</span></p>
