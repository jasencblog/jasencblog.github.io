---
layout: post
title:  "Web Presence"
date:   2015-08-17
---

## Resume Website

As I alluded to in a previous post I have created a
[resume website](http://www.jasencarroll.com) and rearranged my sites. I've been
thinking of putting together a portfolio for a long time now but always kept
pushing it off - mostly because I wanted to have the perfect suite of apps and
the perfect styles and the perfect everything to show the work I'm capable of.
Oh and not to mention the perfect glamorous portfolio site as well.

After finishing the second project of the FSND (I'm waiting to finish some
extra features before reviewing here) I started poking around their [Front End
Developer Nanodegree](https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001)
and decided to work on their Resume Project. It was a nice transition to focus
on some familiar things after coming out of a database wormhole.

### The Work

After being provided with a few files I was to create a dynamically generated
website using JavaScript while saving all of the necessary user data for my
site in JSONs. I made a lot of changes to the provided files to really tailor
them to my liking. I almost entirely rewrote the CSS, and was thinking of going
to Sass before deciding to keep complexity down. At first I added a CSS reset
but then decided to go with the HTML5 Boilerplate and just use Normalize. From
there I used everything I could in the boilerplate, Modernizer, a hosted jQuery
with a back up local version, registered my site for Google Analytics.

As I started publishing my site and making sure it was working on my iPhone
correctly I noticed a lot of things weren't displaying correctly, most
notably anything that was using a `.flex-box` or `.flex-item`. I promptly
removed flex from my project and went with simple `<ul>` and `<li>` where
needed. Ah, that looks much better.

### The Reflection

I'm glad I went with this project and more of a resume site than a portfolio.
Considering I am more interested in being a full stack or backend programmer
it wouldn't make much sense to have a glitzy portfolio showing off all of
my front end capabilities.

In the end I got a lot more comfortable with JSON and using JavaScript to
extract all of the information and display it on a web page. It was nice doing
this project for personal reasons as opposed to another project that was going
to be evaluated, and it really inspired me to make sure everything was
hosted and displaying properly across devices.

And at the end of the day, updating any part of my resume is as simple as
changing some content in a JSON and pushing `master`.
