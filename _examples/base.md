---
title: 'Example: no `srcset`'
image:
  - src: example-1.jpg
    alt: 'Leaves and a blue sky.'
  - src: example-2.jpg
    alt: 'Fall leaves on the ground at sunset, with a dog walking in the background.'
---

{% assign image = page.image[0] %}
{% include image.html %}

{% assign image = page.image[1] %}
{% include image.html %}
