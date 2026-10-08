---
layout: default
title: About
permalink: /
description: Zhaocheng Pu's personal website, with projects and certificates.

# Photos for the "Moments" section. Images live in assets/img/moments/.
moments:
  - path: assets/img/moments/cooking.jpg
    alt: Zhaocheng in the kitchen, holding up a bite of a home-cooked dish with chopsticks
  - path: assets/img/moments/tea.jpg
    alt: Zhaocheng smiling and raising a cup of tea at a restaurant
  - path: assets/img/moments/katsudon.jpg
    alt: Zhaocheng with hands together before eating a bowl of katsudon
  - path: assets/img/moments/dinner.jpg
    alt: Zhaocheng holding chopsticks at a restaurant table
---

<div class="home">
  <section class="home-hero">
    <div class="home-hero-photo">
      {% include figure.liquid loading="eager" path="assets/img/zhaocheng-profile.jpg" sizes="200px" alt="Photo of Zhaocheng Pu" cache_bust=true %}
    </div>
    <div class="home-hero-text">
      <p class="home-hello">Hi there <span aria-hidden="true">👋</span></p>
      <h1 class="home-name">{{ site.first_name }} {{ site.last_name }}</h1>
      <p class="home-intro">Welcome to my little corner of the internet. I'm just getting started, so this space will grow as I learn and build. <span aria-hidden="true">🌱</span></p>
      <nav class="social-links" aria-label="Social links">
        {% for social in site.data.socials %}
          {% case social[0] %}
            {% when 'email' %}
              {% capture link_url %}mailto:{{ social[1] | encode_email }}{% endcapture %}
              {% assign link_title = 'Email' %}
              {% assign link_icon = 'fa-solid fa-envelope' %}
            {% when 'linkedin_username' %}
              {% capture link_url %}https://www.linkedin.com/in/{{ social[1] }}{% endcapture %}
              {% assign link_title = 'LinkedIn' %}
              {% assign link_icon = 'fa-brands fa-linkedin' %}
            {% when 'github_username' %}
              {% capture link_url %}https://github.com/{{ social[1] }}{% endcapture %}
              {% assign link_title = 'GitHub' %}
              {% assign link_icon = 'fa-brands fa-github' %}
            {% else %}
              {% assign link_url = social[1].url %}
              {% assign link_title = social[1].title %}
              {% assign link_icon = social[1].logo %}
          {% endcase %}
          <a class="social-link" href="{{ link_url }}" rel="me noopener" {% unless social[0] == 'email' %}target="_blank"{% endunless %}>
            <i class="{{ link_icon }}" aria-hidden="true"></i>
            <span>{{ link_title }}</span>
          </a>
        {% endfor %}
      </nav>
    </div>
  </section>

{% assign latest_certificate = site.data.certificates | first %}
{% if latest_certificate %}

  <section class="home-section">
    <div class="section-heading">
      <h2>Latest certificate</h2>
      <a class="section-more" href="{{ '/certificates/' | relative_url }}">All certificates <span aria-hidden="true">→</span></a>
    </div>
    <a class="cert-highlight" href="{{ '/certificates/' | relative_url }}">
      <div class="cert-highlight-image">
        {% include figure.liquid path=latest_certificate.image sizes="(min-width: 576px) 220px, 90vw" alt="Certificate preview" %}
      </div>
      <div class="cert-highlight-body">
        <p class="cert-issuer">
          {% if latest_certificate.issuer_icon %}<i class="{{ latest_certificate.issuer_icon }}" aria-hidden="true"></i>{% endif %}
          {{ latest_certificate.issuer }}
        </p>
        <h3 class="cert-title">{{ latest_certificate.title }}</h3>
        <p class="cert-date">Issued {{ latest_certificate.date | date: '%B %-d, %Y' }}</p>
        <span class="card-more">See details <span aria-hidden="true">→</span></span>
      </div>
    </a>
  </section>
{% endif %}

{% if page.moments.size > 0 %}

  <section class="home-section">
    <div class="section-heading">
      <h2>Moments</h2>
    </div>
    <div class="moments-grid">
      {% for photo in page.moments %}
        {% assign photo_base = photo.path | remove: '.jpg' | remove: '.jpeg' | remove: '.png' %}
        <div class="moment">
          <img
            src="{{ photo.path | relative_url }}"
            {% if site.imagemagick.enabled %}
              srcset="{% for width in site.imagemagick.widths %}{{ photo_base | relative_url }}-{{ width }}.webp {{ width }}w{% unless forloop.last %}, {% endunless %}{% endfor %}"
              sizes="(min-width: 880px) 200px, 45vw"
            {% endif %}
            data-zoom-src="{{ photo.path | relative_url }}"
            data-zoomable
            loading="lazy"
            width="1200"
            height="1600"
            alt="{{ photo.alt }}"
          >
        </div>
      {% endfor %}
    </div>
  </section>
{% endif %}
</div>
