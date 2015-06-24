---
layout: post
title:  "Broken Computer? Installment 1"
date:   2015-06-23 22:15:32
---
I had previously set up my computer for Ruby on Rails thanks to [Installfest](http://installfest.railsbridge.org/installfest/). I went to use it again and somehow was back to Ruby 2.0 and no Rails to be found. Puzzled I simply reinstalled everything. I noticed the real trouble when I tried opening a new terminal window and couldn't run a Rails server. I checked all of my versions and somehow was back to Ruby 2.0 and no Rails to be found.

> What the shit? I know I put this stuff on here a month or so ago and I know I just followed those instructions explicity again, why is shit disappearing on me?

Frustrated, I had no idea how to trouble shoot this. Google "disappearing rails"? I started writing a post on Stack Overlow because I only had another hour left before I had to leave the library. I didn't have any idea what to do and by the time I had been able to at least try to define my problem and make it a logical post an hour went by.

Fried and pretty certain I had permanently ruined any goals of ever doing back end work again I decided to leave the library and pack it in for the day considering my internet wasn't working at home. I started thinking of alternatives, maybe I could get in to iOS and/or Android programming. I walked in my apartment and looked at my phone which had connected to the wifi - my internet was working for the first time in over a week. (This isn't a problem on my end, and I don't have to pay for wifi, so there is really nothing I can do when it goes out.)

Rather than get after it while I was still furious I put my stuff down and went outside for an hour or so. I stayed away from the computer for another hour after that and then decided to get to work.

> Alright, this is going to take a while, hopefully I can make it a few hours without eating.


With the limited knowledge I had and whatever I did find on the internet I noticed that my shell was running in tcsh instead of bash. I forgot about my Stack Overflow post in it's entirety once I found a starting point.

I started prodding in that direction and was allured to install [oh my zsh](http://ohmyz.sh/). This fixed my terminal prompt, but the disappearing Rails was still a thing. After uninstalling oh my zsh I learned that what I was really after was bash. So I set my terminal back to bash.

But things were still all goofy and the styles of oh my zsh were left behind. I remember previously tinkering with those files and remembered I set a dependency for bash_profile to simply reference bashrc so I decided to delete bash_profile and try a reboot. (Thinking maybe if I was lucky the system would auto reinstall with default values - NOPE.) Not only are computers not magical all the time, but it turns out I remembered my dependency incorrectly. My bashrc referenced bash_profile.

At least I'm making progress. I read all about setting my $PATH all over again. I lfound this artcile to explain [bash_profile vs bashrc](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html). I found an article that explains how to color your terminal. (Can't find reference for this, at least not the one I used.) And went to bed after two and a half hours, leaving some tabs open and a notecard with all of my next steps.

 One last thing I did before I went to bed was install rvm one last time. I woke up in the morning and it was still there! I set a new $PATH, understood what it was changing, and almost how. So then I found the $PATH that would display what I wanted. And at the end of it all I colored everything to be much more enjoyable colors than I had before. All within 15 minutes.

>Thank you Google and Stack Overflow, let's break all of the things and then put them back together.

I still don't know how I got on tcsh in the first place, I have some scenarios to test out though next time I feel like breaking something on my own accord.
