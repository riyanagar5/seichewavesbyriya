---
layout: default
title: Archives
---

<div class="page-content">
  <h1>Archives</h1>
  {% assign all_posts = "" | split: "" %}
  {% assign all_posts = all_posts | concat: site.essays %}
  {% assign all_posts = all_posts | concat: site.memos %}
  {% assign all_posts = all_posts | concat: site.papers %}
  {% assign sorted_posts = all_posts | sort: "date" | reverse %}

  <ul class="post-list">
    {% for post in sorted_posts %}
      <li>
        <a class="post-title-link" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
      </li>
    {% endfor %}
  </ul>
</div>
