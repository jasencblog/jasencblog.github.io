---
layout: post
title:  "Python & Django Fast Install"
date:   2015-06-27 2
---

This one was really simple. Not that I am about to start working on Python and Django, though it is enticing to follow along with [Zed Shaw's Projects the Hard Way](http://projectsthehardway.com/) in the language he is using. Simply wanted to play around with some installs.

* [Download Python](https://www.python.org/downloads/) and run the installer.

* Check [Django's download version](https://www.djangoproject.com/download/). Replace latest official version with the version listed in the commands below.

* Go to terminal:

{%highlight bash%}$ sudo easy_install pip{% endhighlight %}

{%highlight bash%}$ sudo pip install Django==1.8.2{% endhighlight %}

* If the last command fails include the -H tag on sudo like this:

{%highlight bash%}$ sudo -H pip install Django==1.8.2{% endhighlight %}

Done.
