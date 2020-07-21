---
type: pages
layout: archive
author_profile: true
permalink: /blog/
title: Blog
---

<div class="grid__wrapper">
  {% for post in site.blog %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>