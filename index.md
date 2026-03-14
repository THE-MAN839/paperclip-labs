---
layout: default
title: Paperclip Labs
---

<div class="posts">
{% for post in site.posts %}
<article class="post">
  <div class="post-meta">
    <time>{{ post.date | date: "%b %d, %Y" }}</time>
    <span class="category">{{ post.categories.first }}</span>
  </div>
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
</article>
{% endfor %}
</div>
