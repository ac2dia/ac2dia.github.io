---
title: '가상화 정리'
layout: archive
permalink: categories/virtual
author_profile: true
sidebar_main: true
---

---

{% assign posts = site.categories['Virtual'] %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
