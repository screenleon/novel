---
layout: default
title: "時光回音 — 系列索引"
---

# 時光回音（Time-Echo）

以下列出本系列章節（依章號排序）。若要顯示草稿，請在 `_config.yml` 將 `show_drafts` 改為 true。

{% assign chapters = site.novels | where: "series", "time-echo" | sort: "chapter" %}
<ol>
{% for c in chapters %}
  {% if c.status == "draft" and site.show_drafts != true %}
    <li>第{{ c.chapter }}章：{{ c.title }} <em>(draft)</em></li>
  {% else %}
    <li><a href="{{ c.url | relative_url }}">第{{ c.chapter }}章：{{ c.title }}</a> — {{ c.excerpt }}</li>
  {% endif %}
{% endfor %}
</ol>
