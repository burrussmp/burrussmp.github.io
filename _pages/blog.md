---
layout: archive
author_profile: true
permalink: /blog/
title: Blog
header:
  og_image: /assets/images/website_feature_image.png
  overlay_image: /assets/images/header-image-2.png
  caption: Copyright © Matthew Burruss
---

<div class="grid__wrapper">
  <h3 class="archive__subtitle">By Category</h3>
  <a class= "category-button c" href="/categories/data-visualization">Data Visualizations</a>
  <a class= "category-button d" href="/categories/machine-learning">Machine Learning</a>
  <a class= "category-button f" href="/categories/statistics">Statistics</a>
  <a class= "category-button g" href="/categories/computer-vision">Computer Vision</a>
  <a class= "category-button h" href="/categories/artificial-intelligence">Artificial Intelligence</a>
  <a class= "category-button b" href="/categories/augmented-reality">Augmented Reality</a>
  <a class= "category-button a" href="/categories/opinions">Opinion</a>
  <a class= "category-button d" href="/categories/other">Other</a>
</div>

{% assign blogs = site.posts | sort: 'date' | reverse  %}
<div class="grid__wrapper">
  <h3 class="archive__subtitle">All Posts</h3>
  {% for post in blogs %}
    {% include archive-single.html type="list" %}
  {% endfor %}
</div>