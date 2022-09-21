title: "Airbnb" # 카테고리 이름
layout: archive
permalink: categories/CloneCoding
author_profile: true
sidebar_main: true

---

{% assign posts = site.categories.CloneCoding %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
