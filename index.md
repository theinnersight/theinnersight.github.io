---
layout: default
---

<style>
  @import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,500;0,600;1,500&display=swap');

  .is-hero {
    text-align: center;
    margin: 2.5rem 0 3rem;
  }
  .is-eyebrow {
    font-size: 0.72rem;
    letter-spacing: 0.28em;
    text-transform: uppercase;
    color: #7a708c;
    margin-bottom: 0.4rem;
  }
  .is-title {
    font-family: 'Cormorant Garamond', Georgia, serif;
    font-weight: 500;
    font-size: 3rem;
    letter-spacing: 0.12em;
    color: #241f38;
    margin: 0;
    line-height: 1.1;
  }
  .is-rule {
    width: 3.5rem;
    height: 1px;
    background: #c9a227;
    border: 0;
    margin: 1.1rem auto 0;
  }

  .is-spread {
    list-style: none;
    margin: 0;
    padding: 0;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 1.4rem;
  }
  .is-spread > li { margin: 0; }

  .is-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    aspect-ratio: 5 / 8;
    padding: 1.1rem 0.8rem;
    border-radius: 10px;
    background: linear-gradient(165deg, #2a2344 0%, #1e1b33 60%, #171426 100%);
    border: 1px solid #c9a227;
    box-shadow: inset 0 0 0 4px #1e1b33, inset 0 0 0 5px rgba(201, 162, 39, 0.55);
    text-decoration: none !important;
    transition: transform 0.18s ease, box-shadow 0.18s ease;
  }
  .is-card:hover,
  .is-card:focus-visible {
    transform: translateY(-5px);
    box-shadow: inset 0 0 0 4px #1e1b33, inset 0 0 0 5px rgba(201, 162, 39, 0.55),
      0 10px 22px rgba(30, 27, 51, 0.28);
  }
  .is-card:focus-visible {
    outline: 2px solid #c9a227;
    outline-offset: 3px;
  }

  .is-numeral {
    font-family: 'Cormorant Garamond', Georgia, serif;
    font-size: 1.05rem;
    letter-spacing: 0.18em;
    color: #c9a227;
    text-transform: uppercase;   /* new */
  }
  
  .is-name {
    font-family: 'Cormorant Garamond', Georgia, serif;
    font-style: italic;
    font-weight: 500;
    font-size: 1.45rem;
    color: #f5eedf;
    text-align: center;
    line-height: 1.2;
  }
  
  .is-date {
    font-size: 0.62rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: #9b8ec4;
  }

  .is-back {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 0.6rem;
    aspect-ratio: 5 / 8;
    border-radius: 10px;
    border: 1px dashed rgba(122, 112, 140, 0.55);
    background:
      radial-gradient(circle, rgba(201, 162, 39, 0.28) 1px, transparent 1.6px) 0 0 / 16px 16px,
      #f3f0f8;
  }
  .is-back .is-star {
    font-size: 1.3rem;
    color: #c9a227;
  }
  .is-back span:last-child {
    font-size: 0.62rem;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: #7a708c;
  }

  .is-empty {
    text-align: center;
    color: #7a708c;
    font-style: italic;
  }

  @media (prefers-reduced-motion: reduce) {
    .is-card { transition: none; }
    .is-card:hover, .is-card:focus-visible { transform: none; }
  }
</style>

<header class="is-hero">
  <p class="is-eyebrow">Inner sight, written down</p>
  <h1 class="is-title">The InnerSight</h1>
  <hr class="is-rule">
</header>

{% if site.posts.size == 0 %}
  <p class="is-empty">The deck is unshuffled — no cards drawn yet.</p>
{% else %}
<ol class="is-spread" reversed>
  {% for post in site.categories.tarot %}
  <li>
    <a class="is-card" href="{{ post.url | relative_url }}">
      <span class="is-numeral">{{ post.numeral | default: "✶" }}</span>
      <span class="is-name">{% if post.card %}{% assign w = post.card | split: " " %}{% for word in w %}{% if word == "of" %}of{% else %}{{ word | capitalize }}{% endif %}{% unless forloop.last %} {% endunless %}{% endfor %}{% else %}{{ post.title }}{% endif %}</span>
      <time class="is-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time>
    </a>
  </li>
  {% endfor %}
  <li class="is-back" aria-hidden="true">
    <span class="is-star">✶</span>
    <span>Tomorrow's draw</span>
  </li>
</ol>
{% endif %}
