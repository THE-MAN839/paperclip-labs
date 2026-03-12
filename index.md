---
layout: default
---

<ul class="posts-list">
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}" class="post-link">{{ post.title }}</a>
    <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
    {% if post.excerpt %}
    <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 35 }}</p>
    {% endif %}
  </li>
{% endfor %}
</ul>
