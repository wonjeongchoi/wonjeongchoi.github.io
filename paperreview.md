---
layout: page
title: "Paper Review"
---

# LLM Safety (e.g., Hallucination, Truthfulness)

<style>
  .pr-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
    margin-top: 1rem;
  }
  .pr-card {
    border: 1px solid #e5e7eb;
    border-radius: 14px;
    background: #fff;
    padding: 14px 16px;
    display: flex;
    flex-direction: column;
    gap: 8px;
    transition: transform .12s ease, box-shadow .12s ease;
  }
  .pr-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 22px rgba(0,0,0,.06);
  }
  .pr-title {
    margin: 0;
    font-size: 1.05rem;
    font-weight: 700;
    line-height: 1.35;
  }
  .pr-title a {
    text-decoration: none;
  }
  .pr-subtitle {
    margin: 0;
    font-size: .95rem;
    color: #6b7280;
  }
  .pr-meta {
    margin-top: 2px;
    font-size: .85rem;
    color: #6b7280;
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .pr-tag {
    display: inline-block;
    border: 1px solid #e5e7eb;
    border-radius: 999px;
    padding: 2px 8px;
    font-size: .8rem;
    background: #f9fafb;
  }
</style>

{% assign reviews = site.posts | where_exp:"p","p.categories contains 'paperreview'" %}

<div class="pr-grid">
  {% for post in reviews %}
    {% assign sub = post.subtitle | default: post.sub_title | default: post.tagline %}
    <article class="pr-card">
      <h2 class="pr-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      {% if sub %}
        <p class="pr-subtitle">{{ sub }}</p>
      {% endif %}

      <div class="pr-meta">
        {% if post.tags and post.tags.size > 0 %}
          {% for t in post.tags %}
            <span class="pr-tag">#{{ t }}</span>
          {% endfor %}
        {% endif %}
      </div>
    </article>
  {% endfor %}
</div>
