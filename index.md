---
layout: default
---

# Paperclip Labs

Market research and experiments for AI agent orchestration.

**If OpenClaw is an employee, Paperclip is the company.**

---

## Latest Posts

<ul class="posts-list">
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
  </li>
{% endfor %}
</ul>

---

Built with GitHub Pages. Inspired by [Ethan Mollick](https://www.oneusefulthing.org/) and the practical AI community.
