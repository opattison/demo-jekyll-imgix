# <a href="https://olivermak.es/"><img src="https://olivermak.es/icons/favicon32.svg" width="32" height="32"></a> Responsive `srcset` images with imgix

## [Demo site](http://demo-jekyll-imgix.s3-website-us-east-1.amazonaws.com/)

This is a demo Jekyll site made for a [JekyllConf 2016](http://jekyllconf.com/) lightning talk, presented 2016-05-07.

## [Video of presentation](https://www.youtube.com/watch?v=BIf6oNpGl74)

[View on YouTube](https://www.youtube.com/watch?v=BIf6oNpGl74). Speaking notes are in this repo.

## [Further notes](https://olivermak.es/2016/05/jekyllconf-responsive-images/)

I wrote about my responsive images process to accompany this repo [on my website](https://olivermak.es/2016/05/jekyllconf-responsive-images/).

## Useful links

- A foundational piece by Eric Portis on [implementing responsive images with `srcset` and `sizes`](https://ericportis.com/posts/2014/srcset-sizes/)
- [Responsive Images 101 series](http://blog.cloudfour.com/responsive-images-101-definitions/) by Jason Grigsby (Cloud Four)
- [imgix, the real-time image processing service](http://imgix.com/)
- [jekyll-imgix plugin](https://github.com/imgix/jekyll-imgix)
- [My own Jekyll site](https://github.com/opattison/olivermakes/) (which uses responsive images made faster with imgix) – [check out my photography posts](/photography) for examples of `srcset` and imgix in use

---

## View the demo

[Demo site](http://demo-jekyll-imgix.s3-website-us-east-1.amazonaws.com/)

If you do want to run this demo locally to see how Jekyll and imgix work, I have included a `rake` command for running Jekyll with the jekyll-imgix plugin.

1. Install Ruby
2. run `$ bundle install`
3. run `$ rake serve`

Edit the `_examples` files or play around with the `srcset` values in the `_config.yml` file.

Any questions about this demo? Submit an issue or get in touch [on Twitter: @olivermakes](https://twitter.com/olivermakes).
