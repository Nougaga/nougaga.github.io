---
layout: page
title: Study
---
<h2>R</h2>
<ul class="posts">
    {% for post in site.categories.R %}
      <li><span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
<h2>Python</h2>
<ul class="posts">
    {% for post in site.categories.py %}
      <li><span>{{ post.date | date_to_string }}</span> » <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>