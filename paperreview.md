---
layout: page
title: "Paper Review"
---

<h1>Paper Reviews</h1>

<ul>
  {% for post in site.categories.paperreview %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span style="color: gray; font-size: 0.9em;">({{ post.date | date: "%Y-%m-%d" }})</span>
    </li>
  {% endfor %}
</ul>
