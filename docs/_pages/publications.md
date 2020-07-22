---
type: publications
layout: archive
author_profile: false
permalink: /publications/
title: Publications
tagline: "It ain't much but it's honest work"
header:
  overlay_image: /assets/images/among_sierra_nevada.jpg
  caption: Copyright © Albert Bierdstadt
---

{% assign publications = site.publications | sort: 'date' | reverse  %}
<div>
{% for post in publications %}
  {% include archive-single.html %}
  <hr/>
{% endfor %}
</div>