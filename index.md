---
layout: default
title: "小說總覽"
---

# 小說總覽

首頁只顯示各系列的「部分章節」（預設最新 5 章）。點進系列頁後，才會看到該系列完整章節列表。

{% assign drafts_visible = false %}
{% if site.show_drafts == true or jekyll.environment == "development" %}
  {% assign drafts_visible = true %}
{% endif %}

{% assign novels_with_series = site.novels | where_exp: "n", "n.series" %}
{% assign series_list = novels_with_series | map: "series" | uniq | sort %}
{% for s in series_list %}
  {% assign series_url = "/novels/" | append: s | append: "/" %}
  <h2><a href="{{ series_url | relative_url }}">{{ s }}</a></h2>

  {% assign items = site.novels | where: "series", s | sort: "chapter" | reverse %}
  <ul>
    {% assign shown_count = 0 %}
    {% for item in items %}
      {% if item.status == "draft" and drafts_visible != true %}
        {% continue %}
      {% endif %}

      {% if shown_count >= 5 %}
        {% break %}
      {% endif %}

      <li>
        <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
        {% if item.status == "draft" %} (draft){% endif %}
        {% if item.excerpt %} — {{ item.excerpt }}{% endif %}
      </li>
      {% assign shown_count = shown_count | plus: 1 %}
    {% endfor %}
  </ul>

  <div><a href="{{ series_url | relative_url }}">查看本系列全部章節 →</a></div>
{% endfor %}
