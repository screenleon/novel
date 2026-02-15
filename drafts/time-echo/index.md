---
layout: default
title: "時光回音（草稿）— 系列索引"
permalink: /drafts/time-echo/
---

# 時光回音（草稿）

以下列出本系列草稿章節（依章號排序）。

{% assign chapters = site.drafts | where: "series", "time-echo" | sort: "chapter" %}

<ol>
{% for c in chapters %}
  <li>
    <a href="{{ c.url | relative_url }}">{{ c.title }}</a>
    {% if c.excerpt %} — {{ c.excerpt }}{% endif %}
  </li>
{% endfor %}
</ol>
