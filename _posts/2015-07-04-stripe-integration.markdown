---
layout: post
title:  "Stripe Integration with Rails"
date:   2015-07-04
---

As I eluded to in my last post I was having a hard time getting my Rails application to properly integrate with [Stripe](https://stripe.com/). I had all of the plans set up properly and the free form was working correctly. I just couldn't get the paid plan to work.

I really didn't want to destroy this branch and start over again. I've done that once before and didn't like the feeling of not knowing what was wrong so I wanted to learn this time. As well as the fact that I had no idea how far back I had to go in git history, so it might not have been time beneficial anyway.

At first my Rails server told me that my stripe_card_token was undefined. I couldn't find very much on this topic, the few things I could find showed a similar set up to what I had, so I decided to try moving on to something else.

I was at an utter loss so I emailed Stripe support to see if they would be able to provide any tips while I continued to troubleshoot on my own. Before they got back to me I checked my logs at Stripe and noticed that the card data just wasn't being sent at all, which explained why the pro sign up wouldn't work but the free sign up was working fine - the free sign up didn't require a credit card. When support did get back to me they confirmed the same thing, they weren't receiving any card data.

So off to my JS file that handled the form processing to Stripe. I started trying to debug there but wasn't able to get very far other than making sure my jQuery variables were set and capturing the card data properly. I concluded it might be my Stripe.createToken but didn't know how to check.

Luckily after posing a few questions in various places I was able to get connected with [Patrick Biegel](http://codecanyon.net/user/Blackneron/portfolio) who has a CodeCanyon portfolio with a few applications that he built. Patrick took the time to write a very commented debug version of my code. As soon as I loaded it up I realized that the JS file was never getting the STRIPE_PUBLIC_KEY from the meta tag on my application.html.erb. I immediately header over to the meta tag and realized I was supplying "STRIPE_PUBLIC_KEY" as a string instead of a global variable.

Deleted those quotation marks and everything worked flawlessly. It would have taken me forever to find that without Patrick's help, if I ever found it at all. Plus I learned some debugging along the way!
