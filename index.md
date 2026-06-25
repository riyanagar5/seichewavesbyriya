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

<h2 class="section-title section-title-bold">Read, Ponder and Question</h2>

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
          <p class="grid-card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
          <h3>{{ post.title }}</h3>
          <p>{{ post.description }}</p>
          <span class="read-more">Read more &rarr;</span>
        </div>
      </a>
    {% endfor %}
  </div>

  {% assign featured_page2 = featured | slice: 3, 3 %}
  <div class="post-grid carousel-page" data-page="1" hidden>
    {% for post in featured_page2 %}
      <a class="grid-card" href="{{ post.url | relative_url }}">
        <img src="{{ post.thumbnail | default: '/assets/images/placeholder-thumb.jpg' | relative_url }}" alt="">
        <div class="grid-card-body">
          <p class="grid-card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
          <h3>{{ post.title }}</h3>
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

  {% if featured_page2.size > 0 %}
    <div class="carousel-dots">
      <button class="carousel-dot active" data-goto="0" aria-label="Show articles 1 to 3"></button>
      <button class="carousel-dot" data-goto="1" aria-label="Show articles 4 to 6"></button>
    </div>
  {% endif %}
</div>

<script>
  (function() {
    var pages = document.querySelectorAll('.carousel-page');
    var dots = document.querySelectorAll('.carousel-dot');
    if (dots.length < 2) return;
    var current = 0;
    var autoTimer;

    function showPage(idx) {
      pages.forEach(function(p, i) { p.hidden = (i !== idx); });
      dots.forEach(function(d, i) { d.classList.toggle('active', i === idx); });
      current = idx;
    }

    function next() {
      showPage((current + 1) % pages.length);
    }

    function startAuto() {
      autoTimer = setInterval(next, 8000);
    }

    dots.forEach(function(dot) {
      dot.addEventListener('click', function() {
        clearInterval(autoTimer);
        showPage(parseInt(dot.getAttribute('data-goto'), 10));
        startAuto();
      });
    });

    startAuto();
    startAuto();
  })();
</script>

<p class="quote-intro">My favourite quotes for thought ...</p>

<div class="quote-banner quote-banner-sm">
  <img src="{{ '/assets/images/waves-banner.jpg' | relative_url }}" alt="Waves">
  <div class="quote-banner-overlay">
    <blockquote id="rotating-quote">
      "The future belongs to those who believe in the beauty of their dreams"
    </blockquote>
  </div>
</div>

<script>
  (function() {
    var quotes = [
      { text: "The future belongs to those who believe in the beauty of their dreams", author: "Eleanor Roosevelt" },
      { text: "The sea, once it casts its spell, holds one in its net of wonder forever.", author: "Jacques Cousteau" },
      { text: "We are all in the gutter, but some of us are looking at the stars.", author: "Oscar Wilde" }
    ];
    var el = document.getElementById('rotating-quote');
    if (!el) return;
    var i = 0;
    function render() {
      el.innerHTML = '"' + quotes[i].text + '"<cite>&mdash; ' + quotes[i].author + '</cite>';
    }
    render();
    setInterval(function() {
      i = (i + 1) % quotes.length;
      render();
    }, 5000);
  })();
</script>

{% include subscribe.html %}

{% include contact.html %}
