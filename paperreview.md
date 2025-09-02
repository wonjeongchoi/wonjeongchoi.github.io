---
layout: page
title: "Paper Review"
---

# LLM Safety 

<style>
  .pr-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-top: 1rem;
  }
  .pr-card {
    display: flex;
    flex-direction: row;
    align-items: center;
    border: 1px solid #e5e7eb;
    border-radius: 12px;
    background: #fff;
    padding: 14px 18px;
    gap: 18px;
    transition: transform .12s ease, box-shadow .12s ease;
  }
  .pr-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 18px rgba(0,0,0,.06);
  }
  .pr-content {
    display: flex;
    flex-direction: column;
    gap: 6px;
    flex: 1;
  }
  .pr-title {
    margin: 0;
    font-size: 1.1rem;
    font-weight: 700;
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

<div class="pr-list">
  {% for post in reviews %}
    {% assign sub = post.subtitle | default: post.sub_title | default: post.tagline %}
    <article class="pr-card">
      <div class="pr-content">
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
      </div>
    </article>
  {% endfor %}
</div>
