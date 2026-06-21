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

<h2 class="section-title">Read, Ponder, Question the Waves</h2>

{% assign featured = "" | split: "" %}
{% assign featured = featured | concat: site.essays %}
{% assign featured = featured | concat: site.memos %}
{% assign featured = featured | concat: site.papers %}
{% assign featured = featured | where: "featured", true %}
{% assign featured = featured | sort: "date" | reverse %}

<div class="post-grid">
  {% for post in featured limit: 9 %}
    <a class="grid-card" href="{{ post.url | relative_url }}">
      <img src="{{ post.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
      <div class="grid-card-body">
        <p class="grid-card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
        <h3>{{ post.title }}</h3>
        <p>{{ post.description }}</p>
        <span class="read-more">Read more &rarr;</span>
      </div>
    </a>
  {% endfor %}

  {% if featured.size == 0 %}
    <p><em>No featured posts yet. Add <code>featured: true</code> to a post's front matter to feature it here.</em></p>
  {% endif %}
</div>

<div class="quote-banner">
  <img src="{{ '/assets/images/waves-banner.jpg' | relative_url }}" alt="Waves">
  <div class="quote-banner-overlay">
    <blockquote>
      "The future belongs to those who believe in the beauty of their dreams"
      <cite>&mdash; Eleanor Roosevelt</cite>
    </blockquote>
  </div>
</div>

{% include subscribe.html %}

{% include contact.html %}
