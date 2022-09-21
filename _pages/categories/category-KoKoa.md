---
title: "KoKoa" # 카테고리 이름 , 위의 제목
layout: archive
permalink: categories/KoKoa #그냥 카테고리 명
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.KoKoa %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
