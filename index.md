---
layout: default
title: "小說總覽"
---

# 小說總覽

以下為儲存在 collection `novels` 中的作品（依系列分組）。

{% assign series_list = site.novels | map: "series" | uniq %}
{% for s in series_list %}
  <h2>{{ s }}</h2>
  <ul>
    {% assign items = site.novels | where: "series", s | sort: "chapter" %}
    {% for item in items %}
      {% unless item.status == "draft" and site.show_drafts != true %}
        <li><a href="{{ item.url | relative_url }}">{{ item.title }}</a>{% if item.excerpt %} — {{ item.excerpt }}{% endif %}</li>
      {% endunless %}
    {% endfor %}
  </ul>
{% endfor %}
