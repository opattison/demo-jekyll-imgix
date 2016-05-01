---
title: 'Example: `srcset` plus imgix'
image:
  - src: /images/example-1.jpg
    alt: 'Leaves and a blue sky.'
    quality: 40
  - src: /images/example-2.jpg
    alt: 'Fall leaves on the ground at sunset, with a dog walking in the background.'
    quality: 60
---

{% assign image = page.image[0] %}
{% include srcset-with-imgix.html %}

{% assign image = page.image[1] %}
{% include srcset-with-imgix.html %}
