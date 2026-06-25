---
layout: default
title: Home
---

<section class="intro">
  <div class="intro-text">
    <h1>Salut, c'est Riya!</h1>
    <p>
      I'm Riya, an undergraduate International Relations and Economics student at Ashoka University.
      [Add a few more sentences about yourself here whenever you're ready.]
    </p>
  </div>
  <div class="intro-photo">
    <img src="{{ '/assets/images/profile.jpg' | relative_url }}" alt="Riya Nagar">
  </div>
</section>

<h2 class="section-title">Read, Ponder and Question</h2>

{% assign featured = "" | split: "" %}
{% assign featured = featured | concat: site.essays %}
{% assign featured = featured | concat: site.memos %}
{% assign featured = featured | concat: site.papers %}
{% assign featured = featured | where: "featured", true %}
{% assign featured = featured | sort: "date" | reverse %}

<div class="carousel-wrap">
  <div class="post-grid carousel-page" data-page="0">
    {% for post in featured limit: 3 %}
      <a class="grid-card" href="{{ post.url | relative_url }}">
        <img src="{{ post.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="grid-card-body">
          <div class="grid-card-top-row">
            <p class="grid-card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
            {% if post.tags and post.tags.size > 0 %}
              <div class="tag-row-card">
                {% for tag in post.tags limit: 2 %}
                  {% assign slug = tag | downcase | replace: " ", "-" %}
                  <a class="tag-pill-sm" href="{{ '/tags/' | append: slug | append: '/' | relative_url }}">{{ tag }}</a>
                {% endfor %}
              </div>
            {% endif %}
          </div>
          <h3>{{ post.title }}</h3>
          <p>{{ post.description }}</p>
          <span class="read-more">Read more &rarr;</span>
        </div>
      </a>
    {% endfor %}
  </div>

  <div class="post-grid carousel-page" data-page="1" hidden>
    {% assign featured_page2 = featured | slice: 3, 3 %}
    {% for post in featured_page2 %}
      <a class="grid-card" href="{{ post.url | relative_url }}">
        <img src="{{ post.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="grid-card-body">
          <div class="grid-card-top-row">
            <p class="grid-card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
            {% if post.tags and post.tags.size > 0 %}
              <div class="tag-row-card">
                {% for tag in post.tags limit: 2 %}
                  {% assign slug = tag | downcase | replace: " ", "-" %}
                  <a class="tag-pill-sm" href="{{ '/tags/' | append: slug | append: '/' | relative_url }}">{{ tag }}</a>
                {% endfor %}
              </div>
            {% endif %}
          </div>
          <h3>{{ post.title }}</h3>
          <p>{{ post.description }}</p>
          <span class="read-more">Read more &rarr;</span>
        </div>
      </a>
    {% endfor %}
  </div>

  {% if featured.size == 0 %}
    <p><em>No featured posts yet. Add <code>featured: true</code> to a post's front matter to feature it here, with up to 6 total to fill both carousel pages.</em></p>
  {% endif %}

  {% if featured.size > 3 %}
    <div class="carousel-dots">
      <button class="carousel-dot active" data-goto="0" aria-label="Show articles 1 to 3"></button>
      <button
