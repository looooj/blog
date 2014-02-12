---
layout: page
title: MyBlog
tagline: Supporting tagline
---
{% include JB/setup %}

<p>{{ site.BASE_PATH }}</p>
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ site.BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

