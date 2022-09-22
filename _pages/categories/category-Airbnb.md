---
title: "Airbnb" # 카테고리 이름 , 위의 제목
layout: archive
permalink: categories/Airbnb #그냥 카테고리 명
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Airbnb %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
