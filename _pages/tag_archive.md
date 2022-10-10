---
title: "Tag"
layout: tags
permalink: /tags/
author_pofile: true
sidebar_main: true
---

{% assign posts = site.categories.tags %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
