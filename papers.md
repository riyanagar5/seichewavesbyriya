---
layout: default
title: Papers
---

<div class="page-content">
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
