---
layout: default
---

<p style="font-size: 1.1rem; color: var(--text-light); margin-bottom: 3rem;">
    Market research for AI agent orchestration. If OpenClaw is an employee, Paperclip is the company.
</p>

<h2 style="font-family: -apple-system, sans-serif; font-size: 1.2rem; font-weight: 600; margin-bottom: 1.5rem;">Latest Posts</h2>

<ul class="posts-list">
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}" class="post-link">{{ post.title }}</a>
    <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
    {% if post.excerpt %}
    <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
  </li>
{% endfor %}
</ul>
