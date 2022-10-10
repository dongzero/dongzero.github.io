---
title: "Tag"
layout: archive
permalink: /tags
---

{% assign posts = site.categories.tags %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
