---
layout: default
title: Essays
---

<div class="page-content">
  <img src="{{ '/assets/images/essays-banner.jpg' | relative_url }}" alt="Sea" class="page-banner">

  <h1>Essays</h1>

  {% assign sorted = site.essays | sort: "date" | reverse %}

  <div class="post-grid grid-2">
    {% for item in sorted limit: 4 %}
      <a class="grid-card" href="{{ item.url | relative_url }}">
        <img src="{{ item.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="grid-card-body">
          <p class="grid-card-date">{{ item.date | date: "%b %-d, %Y" }}</p>
          <h3>{{ item.title }}</h3>
          <p>{{ item.description }}</p>
          <span class="read-more">Read more &rarr;</span>
        </div>
      </a>
    {% endfor %}
  </div>

  <h2 class="section-title">All essays</h2>
  <ul class="post-list">
    {% for item in sorted %}
      <li>
        <a class="post-title-link" href="{{ item.url | relative_url }}">{{ item.title }}</a>
        <span class="post-date">{{ item.date | date: "%b %-d, %Y" }}</span>
      </li>
    {% endfor %}
  </ul>
</div>
