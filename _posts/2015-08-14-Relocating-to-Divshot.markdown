---
layout: post
title:  "Relocating to Divshot"
date:   2015-08-14
---

## GitHub Pages

Originally I had this blog hosted using GitHub pages. However I recently decided
to implement a Resume Website - which I'll review in a following post. It makes
more sense to have my resume hosted as my user site with GitHub Pages because
when I host a project page, those projects will use the same subdomain making
everything so much cleaner than appending all of my project pages to a blog
site.

Unfortunately moving a Jekyll generated site to a project page wasn't
generating properly. I noticed that all of the `<link>` tags in the `<head>` of
`index.html` were pointing to the wrong location. I figured if I went through
those links and changed them to effectively display using a `gh-pages` branch
it might throw off my local development from properly generating.

## Divshot

I had wanted to try Divshot for a while now and just didn't have a use for it.
I quickly learned that Divshot is very friendly with Jekyll as well, and I
could even preserve my subdomain of [blog.jasencarroll.com](http://blog.jasencarroll.com/)
while creating a new subdomain with the typical `www` for my resume site.

## The Differences

* GitHub Pages renders your Jekyll site off of the appropriate branch, `master`
  or `gh-pages`, whereas Divshot actually hosts your `_site` folder and has you
  `jekyll build && divshot push`.
* This allows for less branches through git/GitHub as it doesn't matter how
  many times your branches are pushed to, you're not going to update your site
  until you push to Divshot.

## In Hindsight

Now that I know how the `_site` folder is appropriately used, I probably could
have done the same thing for GitHub's `gh-pages` branch. However, this wouldn't
have let me use two different subdomains the way that I am now. And it's always
fun trying out different technology.
