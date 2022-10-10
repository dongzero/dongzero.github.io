---
title: "Java"
layout: archive
permalink: Java
sidebar:
         nav: "sidebar-category"
---


{% assign posts = site.categories.Java %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}