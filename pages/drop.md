---
layout: page
title: 点滴
description: 记录生活，写完美生活
keywords: 生活, 自我, 行外
comments: true
menu: 点滴
permalink: /drop/
---

<!-- > God made relatives. Thank God we can choose our friends. -->

<ul>
{% for link in site.data.links %}
  {% if link.src == 'life' %}
  <li><a href="{{ link.url }}" target="_blank">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>

<!-- > 友情链接 -->

<ul>
{% for link in site.data.links %}
  {% if link.src == 'www' %}
  <li><a href="{{ link.url }}" target="_blank">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>
