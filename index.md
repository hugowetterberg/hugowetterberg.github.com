---
layout: page
title: Latest posts
tagline: Supporting tagline
---
{% include JB/setup %}

{% for post in site.posts %}
  <span>{{ post.date | date_to_string }}</span>
  <h3><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h3>
{% endfor %}

