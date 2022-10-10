---
title: "Posts by Category"
layout: archive
permalink: /categories
---

{% assign posts = site.categories.categories %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
