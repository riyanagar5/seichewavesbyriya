---
layout: default
title: Papers
---

<div class="page-content">
  {% assign all_tags = site.papers | map: "tags" | join: "," | split: "," | uniq | sort %}
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

  <h1>Papers</h1>

  {% assign sorted = site.papers | sort: "date" | reverse %}

  <ul class="paper-list">
    {% for item in sorted %}
      <li class="paper-item">
        <img src="{{ item.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="paper-item-body">
          <h3><a href="{{ item.url | relative_url }}">{{ item.title }}</a></h3>
          <span class="post-date">{{ item.date | date: "%b %-d, %Y" }}</span>
          <p>{{ item.description }}</p>
          <a class="read-more" href="{{ item.url | relative_url }}">Read more &rarr;</a>
        </div>
      </li>
    {% endfor %}
  </ul>
</div>
