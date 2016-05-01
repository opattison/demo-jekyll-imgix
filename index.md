---
title: 'Demo: Responsive images with Jekyll and imgix'
layout: default
permalink: /
---

<ul>
{% assign examples = site.examples %}
{% for example in examples %}
  <li><a href="{{ example.url }}">{{ example.title }}</a></li>
{% endfor %}
</ul>
