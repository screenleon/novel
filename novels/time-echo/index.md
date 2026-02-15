---
layout: default
title: "時光回音 — 系列索引"
---

# 時光回音（Time-Echo）

以下列出本系列章節（依章號排序）。

{% assign drafts_visible = false %}
{% if site.show_drafts == true or jekyll.environment == "development" %}
  {% assign drafts_visible = true %}
{% endif %}

{% assign chapters = site.novels | where: "series", "time-echo" | sort: "chapter" %}
<ol>
{% for c in chapters %}
  {% unless c.status == "draft" and drafts_visible != true %}
    <li><a href="{{ c.url | relative_url }}">{{ c.title }}</a> — {{ c.excerpt }}</li>
  {% endunless %}
{% endfor %}
</ol>
