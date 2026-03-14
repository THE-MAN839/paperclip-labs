---
layout: default
---

<div id="all-posts">
{% for post in site.posts %}
<article class="post-item" data-category="{{ post.categories.first }}">
    <div class="post-date">{{ post.date | date: "%b %d" }}</div>
    <h2 class="post-title">
        <a href="{{ post.url }}">{{ post.title }}</a>
    </h2>
    <div class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 25 }}</div>
    <div class="post-category">{{ post.categories.first }}</div>
</article>
{% endfor %}
</div>

<style>
#all-posts { padding: 2rem 0; }
.post-item { margin-bottom: 2.5rem; padding-bottom: 2rem; border-bottom: 1px solid #f0f0f0; }
.post-date { color: #999; font-size: 0.85rem; margin-bottom: 0.5rem; }
.post-title { font-size: 1.5rem; margin-bottom: 0.75rem; font-weight: 600; }
.post-title a { color: #222; text-decoration: none; }
.post-title a:hover { color: #d4737e; }
.post-excerpt { color: #555; line-height: 1.6; margin-bottom: 0.5rem; }
.post-category { display: inline-block; padding: 0.2rem 0.6rem; background: #f9e5e7; color: #d4737e; border-radius: 4px; font-size: 0.75rem; }
</style>
