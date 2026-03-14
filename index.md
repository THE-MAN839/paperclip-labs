---
layout: default
title: Home
---

<div id="posts-list">
{% for post in site.posts %}
<article class="post-item">
    <div class="post-meta">
        <time>{{ post.date | date: "%b %d, %Y" }}</time>
        <span class="category-tag">{{ post.categories.first }}</span>
    </div>
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
</article>
{% endfor %}
</div>
