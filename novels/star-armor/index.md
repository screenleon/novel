---
layout: default
title: "星甲 — 系列索引"
---

# 星甲（Star-Armor）

以下列出本系列章節（依章號排序）。

{% assign chapters = site.novels | where: "series", "star-armor" | sort: "chapter" %}
<ol>
{% for c in chapters %}
  {% unless c.status == "draft" and site.show_drafts != true %}
    <li><a href="{{ c.url | relative_url }}">{{ c.title }}</a> — {{ c.excerpt }}</li>
  {% endunless %}
{% endfor %}
</ol>
