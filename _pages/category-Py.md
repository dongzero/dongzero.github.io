---
title: "Pyhton"
layout: archive
permalink: Pyhton
sidebar:
         nav: "sidebar-category"
---


{% assign posts = site.categories.Pyhton %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}