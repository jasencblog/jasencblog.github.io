---
layout: post
title:  "FSND: Project I"
date:   2015-07-29
---

## A Brief Ramble

First I will start by addressing the fact that I haven't given this blog as much
attention as I was hoping to. I've been staying pretty busy to say the least.

With that said I completed my first project of the [Full Stack Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004).
However, don't let the name fool you. This is really Udacity's Back End
offering. In order to truly be considered Full Stack you'd have to accomplish
the front end either on your own or using the Udacity [Front End Nanodegree](https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001).

I had the prerequisites down for the "Full Stack" program and the projects were
more interesting to me so that is where I decided to start. Perhaps one day I
will go back and do the projects from the Front End, or maybe I'll move in a
different direction.

## A Udacity Nanodegree Structure Ramble

Upon starting a Nanodegree you are quickly presented with a list of your to-dos.
Courses are not a part of that list. Instead your projects are just sitting
there waiting for you to get started. Once you click a project you're given a
brief description of the project, a button to submit, a button to view the
instructions, then underneath that is the links to the relevant courses that
will help you accomplish that project - should you need to learn.

It's almost as if Udacity expects people with random experience to be using
their program simply for the projects and feedback...

## Finally, Project I

[Movie Trailers](http://blog.jasencarroll.com/movie_trailers/)

This is a dynamically generated site using server-side code, Python, to host
some movie trailers. The files provided include a Python program that generates
some bare bones HTML, CSS and JavaScript.

### The Assignment

* Create a class for instantiating movie objects that takes at minimum:
  * The title for the movie.
  * The poster/box art for the movie.
  * The trailer for the movie.
* Instantiate several movie objects.
* Manually provide a list of the movies to the functions in the files provided.

### My Improvements

* Added the following additional information to the Movie class:
  * Release date
  * Director
  * Movie synopsis
* Created a list within the class Movie to keep track of every instance,
provided this list to the provided functions.
* Removed inline CSS and JavaScript, placed them in separate files.

#### HTML
The provided Python file generates all necessary HTML to display the minimum
information listed above. I added places to implement my additional information.

#### CSS
The provided inline CSS styles were very basic. Since they used Bootstrap, and
I'm familiar with it, it was very easy to customize the styles to my liking.

* Inverted Navbar colors
* Changed background color
* Inverted movie tile on hover color
* Addressed any font colors as a result
* Added Open Sans to make it all beautiful

#### JavaScript
Other than pulling this in to it's own file I largely left this alone. Otherwise
here is what it does:

* A function is used to ensure the playback of the movie trailer is stopped
when the modal is closed.
* A function is used to get the movie trailer URL and display everything properly.
* On `$(document).ready()` a function is run to provide the sweet animation you
see while the page loads.

#### fresh_tomatoes.py
This is the file that is provided with the project. I could get in to all of the
nifty little features this program has but it's getting late and this post has
become way too long as it is. Maybe I will spill all of Udacity's secrets and my
upgrades some other time.

### Biggest Takeaways

* Learn how to write great README files.
* Start taking style guides seriously. Even if implementing them breaks your
code, you need to find the workaround.
