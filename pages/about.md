---
layout: page
title: About
description: 春天该很好!
keywords: 关于, Tffeb
comments: true
menu: 关于
permalink: /about/
---

> 该blog创建于2019-06，于2020-10-07更换jekyll主题改编

渴望技术，渴望生活 ----Tffeb

好记性不如烂笔头，我一直都在，选择IT，选择前端，从不后悔，把生活，技术记录起来，写出自己的想法与见解，不断提升自我，做一个让自己满意的人!


##### Skill Keywords

{% for skill in site.data.skills %}
###### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}




##### 联系

{% if site.url contains 'tffeb.github.io' %}
<p>
微信：<br />
<img style="height:192px;width:192px;border:1px solid lightgrey;" src="{{ assets_base_url }}/assets/images/qrcode.jpg" alt="Tffeb" />
</p>
{% endif %}

