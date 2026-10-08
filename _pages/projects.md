---
layout: page
title: Projects
permalink: /projects/
description: Things I build, one step at a time.
nav: true
nav_order: 1
---

<div class="project-grid">
  {% assign sorted_projects = site.projects | sort: 'importance' %}
  {% for project in sorted_projects %}
    <a class="project-card" href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">
      {% if project.status %}
        <span class="project-status">{{ project.status }}</span>
      {% endif %}
      <h2 class="project-title">{{ project.title }}</h2>
      <p class="project-description">{{ project.description }}</p>
      <span class="card-more">Read more <span aria-hidden="true">→</span></span>
    </a>
  {% endfor %}
  <div class="project-card project-card-placeholder">
    <span class="project-placeholder-icon" aria-hidden="true">🌱</span>
    <p>More projects coming soon.</p>
  </div>
</div>
