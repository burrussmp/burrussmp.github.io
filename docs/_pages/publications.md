---
type: publications
layout: archive
author_profile: true
permalink: /publications/
title: Publications
---

{% assign publications = site.publications | sort: 'date' | reverse  %}
<div>
{% for post in publications %}
  {% include archive-single.html %}
{% endfor %}
</div>