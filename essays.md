---
layout: default
title: Essays
---

<div class="page-content">
  <img src="{{ '/assets/images/essays-banner.jpg' | relative_url }}" alt="Sea" class="page-banner">

  {% assign all_tags = site.essays | map: "tags" | join: "," | split: "," | uniq | sort %}
  {% if all_tags.size > 0 %}
    <div class="tag-row">
      {% for tag in all_tags %}
        {% if tag != "" %}
          {% assign slug = tag | downcase | replace: " ", "-" %}
          <a class="tag-pill" href="{{ '/tags/' | append: slug | append: '/' | relative_url }}">{{ tag }}</a>
        {% endif %}
      {% endfor %}
    </div>
  {% endif %}

  <h1>Essays</h1>

  {% assign sorted = site.essays | sort: "date" | reverse %}

  <div class="post-grid grid-2">
    {% for item in sorted limit: 4 %}
      <a class="grid-card" href="{{ item.url | relative_url }}">
        <img src="{{ item.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="grid-card-body">
          <div class="grid-card-top-row">
            <p class="grid-card-date">{{ item.date | date: "%b %-d, %Y" }}</p>
            {% if item.tags and item.tags.size > 0 %}
              <div class="tag-row-card">
                {% for tag in item.tags limit: 2 %}
                  {% assign slug = tag | downcase | replace: " ", "-" %}
                  <a class="tag-pill-sm" href="{{ '/tags/' | append: slug | append: '/' | relative_url }}">{{ tag }}</a>
                {% endfor %}
              </div>
            {% endif %}
          </div>
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
