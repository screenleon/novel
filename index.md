---
layout: default
title: "小說總覽"
---

# 小說總覽

以下為儲存在 collection `novels` 中的作品（依系列分組）。若有需要可切換 `show_drafts` 設定以顯示草稿。

{% assign series_list = site.novels | map: "series" | uniq %}
{% for s in series_list %}
  <h2>{{ s }}</h2>
  <ul>
    {% assign items = site.novels | where: "series", s | sort: "chapter" %}
    {% for item in items %}
      {% if item.status == "draft" and site.show_drafts != true %}
        <li>{{ item.chapter }}. {{ item.title }} <em>(draft)</em></li>
      {% else %}
        <li><a href="{{ item.url | relative_url }}">{{ item.chapter }}. {{ item.title }}</a>{% if item.excerpt %} — {{ item.excerpt }}{% endif %}</li>
      {% endif %}
    {% endfor %}
  </ul>
{% endfor %}
