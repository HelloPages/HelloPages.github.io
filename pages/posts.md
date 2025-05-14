---
layout: Post
permalink: /posts
title: Hbw Posts
---

Hbw Posts Hbw Posts Hbw Posts

{% if post.path contains '_posts' %}
  <!-- 显示 _posts 下的文章 -->
{% endif %}

{% for post in site.posts %}
  <!-- 显示文章 -->
{% endfor %}
