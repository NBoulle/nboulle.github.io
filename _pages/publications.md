---
layout: archive
title: "Featured Publications"
permalink: /publications/
author_profile: true
---

<style>
.featured-publications {
  margin: 0 0 2rem;
}

.publications-list-section h2 {
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1.4rem;
  color: #1e2a36;
  border-bottom: 1px solid #dde3ea;
  padding-bottom: 0.5rem;
}

.publication-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}

.publication-card {
  border: 1px solid #dde3ea;
  border-radius: 10px;
  padding: 1rem;
  background: #ffffff;
  box-shadow: 0 2px 6px rgba(15, 23, 42, 0.06);
}

.publication-card-link {
  display: block;
  color: inherit;
  text-decoration: none;
}

.publication-card-link,
.publication-card-link:hover,
.publication-card-link:focus,
.publication-card-link * {
  text-decoration: none !important;
}

.publication-card-link:hover .publication-card-title {
  text-decoration: underline;
}

.publication-card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 0.75rem;
  margin-bottom: 0.55rem;
}

.publication-card-year {
  font-weight: 700;
  color: #56697a;
  font-size: 0.92rem;
}

.publication-card-number {
  font-size: 0.78rem;
  line-height: 1.3;
  color: #70829a;
  font-weight: 700;
  letter-spacing: 0.01em;
  margin-left: auto;
}

.publication-card-venue {
  color: #3f5162;
  font-size: 0.9rem;
  text-align: right;
}

.publication-card-title {
  margin: 0;
  line-height: 1.45;
  color: #1f2f3f;
  font-weight: 600;
}

.publication-card-authors {
  margin: 0.45rem 0 0;
  line-height: 1.5;
  color: #2a3a4a;
}

.publication-link {
  display: inline-block;
  margin-top: 0.65rem;
  font-size: 0.95rem;
}

.publications-list-section {
  margin-top: 2.25rem;
}

.publication-list-rendered {
  display: grid;
  gap: 0.8rem;
}

.pub-entry {
  display: grid;
  grid-template-columns: minmax(0, 1fr);
  gap: 0.55rem;
  border: 1px solid #e5eaf0;
  border-radius: 8px;
  padding: 0.75rem 0.9rem;
  background: #fff;
}

.pub-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 0.75rem;
}

.pub-year {
  font-weight: 700;
  color: #56697a;
  font-size: 0.95rem;
  line-height: 1.4;
}

.pub-number {
  font-weight: 700;
  font-size: 0.72rem;
  color: #70829a;
  letter-spacing: 0.01em;
  margin-left: auto;
}

.pub-arxiv {
  font-size: 0.72rem;
  color: #70829a;
  font-weight: 700;
  letter-spacing: 0.01em;
}

.pub-title {
  margin: 0;
  font-size: 1rem;
  line-height: 1.45;
}

.pub-title a {
  text-decoration: none;
  font-weight: 600;
}

.pub-title a:hover {
  text-decoration: underline;
}

.pub-authors,
.pub-venue {
  margin: 0.25rem 0 0;
  color: #3f5162;
  line-height: 1.45;
}

.pub-arxiv {
  margin: 0.25rem 0 0;
  color: #3f5162;
  line-height: 1.45;
}

@media (max-width: 900px) {
  .publication-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .pub-entry {
    gap: 0.35rem;
  }

  .pub-header {
    flex-wrap: wrap;
  }
}
</style>

<section class="featured-publications">
  <div class="publication-grid">
    {% for pub in site.data.publications.featured %}
    <article class="publication-card">
      {% if pub.arxiv %}
      <a class="publication-card-link" href="{{ pub.arxiv }}">
      {% endif %}
      <div class="publication-card-header">
        <span class="publication-card-year">{{ pub.year }}</span>
        <span class="publication-card-venue">{{ pub.venue }}</span>
      </div>
      <p class="publication-card-title">{{ pub.title }}</p>
      <p class="publication-card-authors">{{ pub.authors }}</p>
      {% if pub.arxiv %}
      </a>
      {% endif %}
    </article>
    {% endfor %}
  </div>
</section>

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

<section class="publications-list-section">
  <h2>List of Publications</h2>
  <div class="publication-list-rendered">
    {% assign total_pubs = site.data.publications.list | size %}
    {% for pub in site.data.publications.list | sort: "year" | reverse %}
    <article class="pub-entry">
      <div class="pub-header">
        <span class="pub-year">{{ pub.year }}</span>
        <span class="pub-number">{{ total_pubs | minus: forloop.index0 }}</span>
      </div>
      <div>
        <p class="pub-title">
          {% if pub.arxiv %}
          <a href="{{ pub.arxiv }}">{{ pub.title }}</a>
          {% else %}
          {{ pub.title }}
          {% endif %}
        </p>
        <p class="pub-authors">{{ pub.authors }}</p>
        {% if pub.venue %}
        <p class="pub-venue">{{ pub.venue }}</p>
        {% elsif pub.arxiv %}
        <p class="pub-venue">arXiv:{{ pub.arxiv | split: "/" | last }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>

<p><b>{{ site.data.publications.thesis.venue }}:</b> <a href="{{ site.data.publications.thesis.url }}">{{ site.data.publications.thesis.title }}</a></p>