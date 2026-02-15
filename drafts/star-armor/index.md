---
layout: default
title: "星甲（草稿）— 系列索引"
permalink: /drafts/star-armor/
---

# 星甲（草稿）

以下列出本系列草稿章節（依章號排序）。

{% assign chapters = site.drafts | where: "series", "star-armor" | sort: "chapter" %}

<ol>
{% for c in chapters %}
  <li>
    <a href="{{ c.url | relative_url }}">{{ c.title }}</a>
    {% if c.excerpt %} — {{ c.excerpt }}{% endif %}
  </li>
{% endfor %}
</ol>
