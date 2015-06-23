---
layout: post
title:  "Broken Computer? Installment 1"
date:   2015-06-23 22:15:32
---
A few days before all of this I realized that my command prompt changed and thought nothing too much of it. Xcode had just updated and I think I may or may not have installed a new OS X version. Uninstalling Xcode and reinstalling seemed to do nothing so I didn't think much of it.

I had previously set up my computer for Ruby and Rails. I went to use them again and somehow was back to Ruby 2.0 and no Rails to be found. Puzzled I simply reinstalled everything. I noticed the real trouble when I tried opening a new terminal window and couldn't run a Rails server. I checked all of my versions and somehow was back to Ruby 2.0 and no Rails to be found.

> "What the shit? I know I put this stuff on here a month or so ago and I know I just followed those instructions explicity again, why is shit disappearing on me?"

Frustrated, I had no idea how to trouble shoot this. Google "disappearing rails"? With the limited knowledge I had and whatever I did find on the internet I noticed that my shell was running in tcsh. I started prodding in that direction and was allured to install [oh my zsh](http://ohmyz.sh/). This fixed my terminal prompt, but the disappearing Rails was still a thing. After uninstalling oh my zsh I learned that what I was really after was bash.

But things were still all goofy and the styles of oh my zsh were left behind. I remember previously tinkering with those files and remembered I set a dependency for .bash to simply reference .bashrc so I decided to delete .bash and try a reboot. (Thinking maybe if I was lucky the system would auto reinstall with default values - NOPE.) Not only are computers not magical all the time, but it turns out I remembered my dependency incorrectly. My .bashrc referenced .bash.

Things got tough, I didn't know how to build my .bash_profile back up. I didn't know how to talk about putting it back together, I just kept finding random examples of people exporting their $PATH and it never worked for me. I created a post on Stack Overflow and had very little help - because I didn't know how to talk about what I was having a problem with.

Fried and pretty certain I had permanently ruined any goals of ever doing back end work again I decided to leave the library and pack it in for the day considering my internet wasn't working at home. I started thinking of alternatives, maybe I could get in to iOS and/or Android programming. I walked in my apartment and looked at my phone which had connected to the wifi - my internet was working for the first time in over a week. (This isn't a problem on my end, and I don't have to pay for wifi, so there is really nothing I can do when it goes out.)

Rather than get after it while I was still upset I put my stuff down and went outside for an hour or so. I stayed away from the computer for another hour after that and then...
