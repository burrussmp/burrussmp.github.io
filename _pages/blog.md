---
layout: archive
author_profile: true
permalink: /blog/
title: Blog
tagline: Topics in machine learning, artificial intelligence, data visualizations, and general tech trends
header:
  og_image: /assets/images/website_feature_image.png
  overlay_image: /assets/images/nighthawks.png
  caption: Copyright © Edward Hopper
---

<div class="grid__wrapper">
  <h3 class="archive__subtitle">Find by Category</h3>
  <a class= "category-button c" href="/categories/datavis">Data Visualizations</a>
  <a class= "category-button d" href="/categories/ml">Machine Learning</a>
  <a class= "category-button f" href="/categories/stats">Statistics</a>
  <a class= "category-button g" href="/categories/cv">Computer Vision</a>
  <a class= "category-button h" href="/categories/ai">Artificial Intelligence</a>
  <a class= "category-button b" href="/categories/ar">Augmented Reality</a>
  <a class= "category-button a" href="/categories/opinions">Opinions</a>
  <a class= "category-button e" href="/categories/other">Other</a>
</div>

{% assign blogs = site.posts | sort: 'date' | reverse  %}
<div class="grid__wrapper">
  <h3 class="archive__subtitle">All Posts</h3>
  {% for post in blogs %}
    {% include archive-single.html type="list" %}
  {% endfor %}
</div>