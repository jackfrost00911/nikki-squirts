---
layout: default
title: From Nikki's Blog | Industry Insights
permalink: /blog/
---

<div class="container" style="max-width: 1000px; margin: 0 auto; padding: 60px 20px;">
  
  <header style="text-align: center; margin-bottom: 60px;" class="reveal">
    <h1 style="font-size: 3rem;">From Nikki's Blog</h1>
    <p style="color: var(--gold); letter-spacing: 2px; text-transform: uppercase;">Insights, Reality Checks, & The Art of the Industry</p>
  </header>

  <div class="blog-grid" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px;">
    {% for post in site.posts %}
    <article class="card reveal" style="display: flex; flex-direction: column; justify-content: space-between;">
      <div>
        <div style="font-size: 0.8rem; color: var(--gold); margin-bottom: 10px;">
          {{ post.date | date: "%b %d, %Y" }} • {{ post.category }}
        </div>
        <h3 style="margin-top: 0;">{{ post.title }}</h3>
        <p style="font-size: 0.9rem; color: var(--text-muted);">{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
      </div>
      <a href="{{ post.url }}" class="readmore" style="color: var(--accent); text-decoration: none; font-weight: 600; margin-top: 20px; display: inline-block;">Read Full Insight →</a>
    </article>
    {% endfor %}
  </div>
</div>
