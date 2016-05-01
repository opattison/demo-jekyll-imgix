# Speaking notes

Hi! I’m Oliver Pattison, an independent designer and developer. This is a quick introduction to implementing responsive images for Jekyll using `srcset`. I will demonstrate how to generate responsive images with Liquid includes, and imgix, an image processing service. Many of us have chosen static sites for their speed, but with some adjustments to our process, we can make them even faster.

## Stats

The heaviest elements on many websites are images. According to the [HTTP Archive][1] **63.5%** of the average page’s weight was made up of images.

*(stats retrieved April 1, 2016, based on the top one million websites)*.

## Uncertainty

There are two key factors of uncertainty when building responsively: the size of a device, and the speed of a network connection. In the spirit of Postel’s [robustness principle][2]: let’s be conservative in what we send.

## Viewport

For example: if a client has a 360 pixel-wide viewport, there usually won’t be a benefit in being served a 1000 pixel-wide image. The costs of serving heavier images to people include:

- slower performance (measured by transfer speeds and memory use)
- and increased bandwidth costs (which is an actual dollar cost for many people – consider metered mobile data plans)

## The solution

Cutting down on the size of served images is one of the most effective methods for improving the perceived performance of an existing site.

We now have a well-supported web standard to help us deal with image weight by serving the right images at the right sizes: `srcset`.

## Block

First, let’s take a look at some reusable code: a building block that we will use throughout this demo.

We assign a variable to the image map/sequence (from the post’s YAML front matter) and then use that variable immediately in a block.

## Why include

Why use an include for images? Flexibility. If we have one or more images specified, the same Liquid include can be used for each of them. If our include gets more complicated (as it certainly will when we add `srcset`), we can add complexity without changing the original content or page metadata.

## Responsive images (without imgix)

### Attributes

`srcset` and `sizes` are attributes of the `<img>` element that combine to give a browser a hint about what it needs to download. `srcset` provides an array of image sources. The `sizes` attribute resembles CSS media queries giving information about image dimensions at various responsive breakpoints *without* having to download an image first. The challenge here is coming up with the right sources and matching sizes.

### Sources

Remember: the browser chooses its source based on the information we provide in these two attributes. The browser often doesn’t know the size of the image in the page.

For the simplicity of this demo, we will use three image source sizes. People have asked me: how many sources do you need? It depends on the case. Each design will have its own requirements for `srcset` and `sizes`.

### Verbosity

This syntax is **verbose**. We can’t help it. We need to give the browser options for sources. Each image has multiple URL paths, providing the browser a hint about the image’s relative size on the page with the `sizes` attribute.

### srcset parts

Let’s use a Liquid loop to generate an image block that matches this simple layout’s responsive behavior.

### sizes

Now let’s define a `sizes` string which will be included (site-wide) in every image block that needs a `sizes` attribute.

### srcset

Let’s also define a default `srcset` sequence. These values will be looped to generate every `srcset` attribute in our demo.

### Image editing

The problem is generating those images: we’ll probably need to use image editing software to generate all of the variants, and then give unique names to each file. For a handful of images this is manageable, but what if our site has lots of images and what if we need *many* `srcset` variants of each image?

## Responsive images with the imgix plugin

### why use imgix

I saw this problem for sites that feature many images. Each image needs multiple sources, meaning potentially hundreds of sources might need to be generated for a single site. Even with automated tools, that is a lot of work and a lot of room for error. It is also work that might need to be re-done if a design is adjusted or specifications change.

### solving the problem

imgix is part of the solution for my projects. What if we could have only one source per image, and from that we could create many variants at different sizes and flexible quality settings? Using URL parameters, or an imgix plugin that generates custom URLs, we can take a single source and then create effectively unlimited variants.

We can also build this into any Jekyll site.

### extend the example

Let’s extend our earlier example which had three source variants.

With some adjustments to the `srcset` Liquid include, the image is now processed by imgix. All variants are generated on request by imgix, and we can even change the parameters if our specifications change.

### saving bytes

In our quest for saving bytes, we made a mistake with our image processing with this JPEG: the quality setting created noticeable compression artifacts in the sky. With a parameter change in the source (specified in the front matter), we can improve the output.

### adjusting quality

Let’s bump the quality from 40 to 70 and then refresh the example page.




## Installing imgix

To see how to configure the imgix plugin for Jekyll, take a look at the documentation for the plugin or review the source for this demo.

Let’s briefly walk through how to install the imgix plugin for a Jekyll site. This assumes that you already have a working Jekyll site, an imgix account and source, and some images that need hosting.

### Gemfile

In your `Gemfile` add the line:

```
gem 'jekyll-imgix'
```

and then run `$ bundle update`.

### Jekyll configuration

In your `_config.yml` file, add:

```
gems:
  - jekyll/imgix

imgix:
  source: YOUR-IMGIX-SOURCE.imgix.net
```

where `YOUR-IMGIX-SOURCE` is the name of your source.


## About imgix

Here are a few important things to know about imgix:

### s3

I recommend Amazon S3 for hosting with imgix, but any web source will do. Make sure you can deploy your site or load your source images before turning on imgix.

### env

The jekyll-imgix plugin does not do anything unless `JEKYLL_ENV`  (the environmental variable) is set to `production`. If the imgix plugin is turned off, a site will *not* fail to build, but images won’t be processed.

### cost

imgix costs money: in my opinion it is well worth it if you’re processing a lot of images and need a CDN to host them. You don’t *need* imgix to process responsive images, but it’s one effective way to do it, and the service has other features worth looking into as well.

---

You can learn more by checking out the repo for this demo on GitHub or reading my recommended resources.

I am [@olivermakes] / <https://olivermak.es> on Twitter and the web – I’m always willing to talk about static sites and excited to see what you’re working on.

---

## Not covering

Things I didn’t cover here but you might want to read up on:

- `<picture>` responsive images (useful for art direction but not as essential for improving performance). You can use `<picture>` and `srcset` together – they are part of the same specification.
- Using [picturefill][3] to polyfill support for responsive images for wider browser support.
- [Cost of imgix][4]: it’s affordable for what it is capable of (but not free after the first month of use). You *can* use one user account for multiple sites.
- Setting up imgix account and sources (covered fully in the [imgix documentation][5]).
- Other capabilities of imgix for art direction.


[1]: http://httparchive.org/interesting.php
[2]: https://en.wikipedia.org/wiki/Robustness_principle
[3]: https://github.com/scottjehl/picturefill
[4]: http://imgix.com/pricing
[5]: https://docs.imgix.com/
