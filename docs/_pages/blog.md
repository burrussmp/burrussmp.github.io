---
type: pages
layout: archive
author_profile: false
permalink: /blog/
title: Blog Posts
tagline: Topics in machine learning, artificial intelligence, data visualizations, and general tech trends
header:
  og_image: /assets/images/website_feature_image.png
  overlay_image: /assets/images/nighthawks.png
  caption: Copyright © Edward Hopper
---
{% assign blogs = site.blog | sort: 'date' | reverse  %}
<div class="grid__wrapper">
  {% for post in blogs %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>