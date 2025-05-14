---
title: 文章归档
layout: Post
permalink: /posts
---

<!-- 文章分类导航（可选） -->
<div class="slot-medium">
  {% assign categories = site.categories | sort %}
  {% for category in categories %}
    {% assign cat_name = category[0] %}
    <a href="/category/{{ cat_name | slugify }}" class="category-link">
      {{ cat_name }}<sup>{{ site.categories[cat_name].size }}</sup>
    </a>
    {% unless forloop.last %}·{% endunless %}
  {% endfor %}
</div>

<!-- 文章主列表 -->
<div class="slot-large">
  <h2>全部文章（共 {{ site.posts.size }} 篇）</h2>
  
  <div class="post-archive">
    {% assign grouped_posts = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
    
    {% for year in grouped_posts %}
      <div class="archive-year">
        <h3 class="year-header">{{ year.name }}</h3>
        
        <ul class="post-list">
          {% assign posts = year.items | sort: 'date' | reverse %}
          {% for post in posts %}
            <li class="post-item">
              <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
                {{ post.date | date: "%m-%d" }}
              </time>
              <a href="{{ post.url }}" class="post-title">{{ post.title }}</a>
              {% if post.tags %}
                <div class="post-tags">
                  {% for tag in post.tags %}
                    <span class="tag">#{{ tag }}</span>
                  {% endfor %}
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </div>
    {% endfor %}
  </div>
</div>

<style>
/* 基础样式 */
.post-archive {
  margin-top: 2rem;
}

.archive-year {
  margin-bottom: 3rem;
}

.year-header {
  color: #666;
  font-size: 1.4rem;
  border-bottom: 1px solid #eee;
  padding-bottom: 0.5rem;
}

/* 文章条目样式 */
.post-list {
  list-style: none;
  padding-left: 0;
}

.post-item {
  display: grid;
  grid-template-columns: 80px 1fr;
  gap: 15px;
  padding: 1rem 0;
  border-bottom: 1px solid #f5f5f5;
}

.post-date {
  color: #888;
  font-size: 0.9rem;
}

.post-title {
  color: #333;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s;
}

.post-title:hover {
  color: #007acc;
}

/* 标签样式 */
.post-tags {
  grid-column: 2 / -1;
  margin-top: 0.3rem;
}

.tag {
  display: inline-block;
  font-size: 0.8rem;
  color: #666;
  background: #f5f5f5;
  padding: 2px 8px;
  border-radius: 3px;
  margin-right: 5px;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .post-item {
    grid-template-columns: 1fr;
  }
  
  .post-date {
    margin-bottom: 0.3rem;
  }
  
  .post-tags {
    grid-column: auto;
  }
}
</style>
