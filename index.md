---
title: 'Demo: Responsive images with Jekyll and imgix'
layout: default
permalink: /
---

<div class="index">

  <ol>
  {% assign examples = site.examples %}
  {% for example in examples %}
    <li><a href="{{ example.url }}">{{ example.title | markdownify | remove: '<p>' | remove: '</p>' }}</a></li>
  {% endfor %}
  </ol>

</div>
