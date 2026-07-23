---
layout: default
title: Past draws
permalink: /draws/
---

<style>
.dr-hero { text-align: center; margin: 2.5rem 0 2.5rem; }
.dr-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-weight: 500;
  font-size: 2.2rem;
  letter-spacing: 0.12em;
  color: #241f38;
  margin: 0;
}
.dr-month {
  font-size: 0.72rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: #7a708c;
  margin: 2.2rem 0 0.4rem;
  font-weight: normal;
}
.dr-row {
  display: flex;
  align-items: baseline;
  gap: 1rem;
  padding: 0.45rem 0;
  border-bottom: 1px solid #e8e2d2;
}
.dr-date {
  font-size: 0.68rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: #9b8ec4;
  min-width: 4.5rem;
}
.dr-card a {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-size: 1.25rem;
  color: #241f38;
  text-decoration: none;
}
.dr-card a:hover { color: #c9a227; }
.dr-numeral {
  margin-left: 0.5rem;
  font-size: 0.75rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #c9a227;
}
.dr-back {
  display: block;
  text-align: center;
  margin-top: 2.5rem;
  font-size: 0.68rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: #7a708c;
  text-decoration: none;
}
.dr-back:hover { color: #c9a227; }
</style>

<header class="dr-hero">
<h1 class="dr-title">Past Draws</h1>
</header>

{% assign prev_month = "" %}
{% for post in site.posts %}
{% assign this_month = post.date | date: "%B %Y" %}
{% if this_month != prev_month %}
<h2 class="dr-month">{{ this_month }}</h2>
{% endif %}
<div class="dr-row">
<time class="dr-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d" }}</time>
<span class="dr-card"><a href="{{ post.url | relative_url }}">{% include cardname.html post=post %}</a>{% if post.numeral %}<span class="dr-numeral">{{ post.numeral }}</span>{% endif %}</span>
</div>
{% assign prev_month = this_month %}
{% endfor %}

<a class="dr-back" href="{{ '/' | relative_url }}">← back to the spread</a>
