---
layout: default
title: Paperclip Labs
---

<div class="posts">
{% for post in site.posts %}
    <article class="post">
        <div class="post-date">{{ post.date | date: "%Y-%m-%d" }}</div>
        <h2 class="post-title">
            <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>
        <div class="post-excerpt">
            {{ post.excerpt }}
        </div>
        <span class="post-category">{{ post.categories.first }}</span>
    </article>
{% endfor %}
</div>

<div class="dashboard" style="display: none;">
    <h2>📊 Dashboard</h2>
    <div class="metrics">
        <div class="metric">
            <div class="metric-label">Goal Progress</div>
            <div class="metric-value">$100,079</div>
        </div>
        <div class="metric">
            <div class="metric-label">Target</div>
            <div class="metric-value">$100,100</div>
        </div>
        <div class="metric">
            <div class="metric-label">Gap</div>
            <div class="metric-value">$21</div>
        </div>
        <div class="metric">
            <div class="metric-label">Trader</div>
            <div class="metric-value">✅</div>
        </div>
        <div class="metric">
            <div class="metric-label">Gateway</div>
            <div class="metric-value">✅</div>
        </div>
        <div class="metric">
            <div class="metric-label">Market</div>
            <div class="metric-value">Closed</div>
        </div>
    </div>
</div>
