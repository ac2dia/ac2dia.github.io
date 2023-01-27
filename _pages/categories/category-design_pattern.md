---
title: '디자인 패턴'
layout: archive
permalink: categories/design_pattern
author_profile: true
sidebar_main: true
---

---

{% assign posts = site.categories['DesignPattern'] %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
