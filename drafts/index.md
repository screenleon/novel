---
layout: default
title: "草稿列表"
permalink: /drafts/
---

# 草稿列表

這裡列出目前放在草稿集合（`_drafts/`）的章節。它們不會出現在首頁與系列正式索引，但會在 GitHub Pages 上輸出成可直接閱讀的頁面。

{% assign items = site.drafts | sort: "date" | reverse %}

{% assign drafts_with_series = items | where_exp: "d", "d.series" %}
{% assign series_list = drafts_with_series | map: "series" | uniq | sort %}

{% for s in series_list %}
  <h2>{{ s }}</h2>
  {% assign series_items = items | where: "series", s | sort: "chapter" %}
  <ol>
  {% for d in series_items %}
    <li>
      <a href="{{ d.url | relative_url }}">{{ d.title }}</a>
      {% if d.excerpt %} — {{ d.excerpt }}{% endif %}
    </li>
  {% endfor %}
  </ol>
{% endfor %}
