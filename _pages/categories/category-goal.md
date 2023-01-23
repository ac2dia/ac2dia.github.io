---
title: '올해의 목표'
layout: archive
permalink: categories/goal
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Goal %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
