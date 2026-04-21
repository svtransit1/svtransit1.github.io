---
layout: default
title: 首页
---

{% for post in site.posts limit: 20 %}
<article>
  <p class="meta"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time></p>
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  {% if post.hero %}<img src="{{ post.hero }}" alt="{{ post.title }}" style="max-height:360px;object-fit:cover;">{% endif %}
  <p>{{ post.excerpt | strip_html | truncate: 200 }}</p>
</article>
<hr>
{% endfor %}
