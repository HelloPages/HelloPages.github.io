---
layout: default
title: 文章列表
---

<div class="post-list">
  {% for post in site.posts %}
    <article class="post-item">
      <a href="{{ post.url | relative_url }}" class="post-link">
        <div class="post-header">
          <h2 class="post-title">{{ post.title }}</h2>
          <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%Y-%m-%d" }}
          </time>
        </div>
      </a>
    </article>
  {% endfor %}
</div>

<style>
.post-list {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.post-item {
  margin-bottom: 2rem;
  border-bottom: 1px solid #eee;
  padding-bottom: 1rem;
}

.post-link {
  text-decoration: none;
  color: inherit;
}

.post-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

.post-title {
  margin: 0;
  font-size: 1.2rem;
  font-weight: 500;
  color: #333;
}

.post-date {
  font-size: 0.9rem;
  color: #666;
  margin-left: 1.5rem;
  flex-shrink: 0;
}

@media (max-width: 600px) {
  .post-header {
    flex-direction: column;
  }
  
  .post-date {
    margin-left: 0;
    margin-top: 0.5rem;
  }
}
</style>
