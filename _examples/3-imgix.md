---
title: 'Example: `srcset` plus imgix'
image:
  - src: /images/example-1.jpg
    alt: 'Leaves and a blue sky.'
    quality: 40 # change this value to a higher or lower value to change the quality of the image
  - src: /images/example-2.jpg
    alt: 'Fall leaves on the ground at sunset, with a dog walking in the background.'
    quality: 60
---

{% assign image = page.image[0] %}
{% include srcset-with-imgix.html %}

{% assign image = page.image[1] %}
{% include srcset-with-imgix.html %}

These images are hosted on an S3 bucket which is connected to an imgix source. If you are using this demo you will not be able to update the S3 or imgix sources but you can test the imgix plugin parameters for the two demo images.
{:.note}
