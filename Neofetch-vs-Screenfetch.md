The goal of this wiki page is to answer the questions:

- How is Neofetch different from Screenfetch?
- What's wrong with Screenfetch?

## Table of Contents

- [Why was Neofetch created?](#why-was-neofetch-created)
- [How does Neofetch differ from Screenfetch?](#how-does-neofetch-differ-from-screenfetch)

## Why was Neofetch created?

Neofetch or as it was originally called `fetch` was never meant to be a replacement for Screenfetch nor was it ever meant to display Ascii logos. Neofetch first started as my `70` line hardcoded script that only supported Arch Linux, only displayed a tiny amount of info and only supported showing images with w3m-img. 

I started posting screenshots of my system to [/r/unixporn/](https://reddit.com/r/unixporn) which included my tiny little script. People started using the script and started asking me to add support for their Linux Distros and later their Operating systems. Me being happy that anyone is using something that I created started adding support various Distros and Operating systems. 

![Oldest screenshot of fetch](https://u.teknik.io/h7KSz.png)
<br \><sub>Oldest screenshot of `fetch`</sub>

When it got to adding support for Mac OS I realized that I had hit a stopping point. The script wasn't written in a way that would allow me to easily expand it to more Operating systems, it needed a rewrite. So I rewrote the script from scratch over an entire weekend and the result is the script base/structure that neofetch is still using today.

I continued to work on Neofetch everyday and whenever someone would suggest a feature, I would add it no questions asked. One day a user by the name of [@aloisdg](https://github.com/dylanaraps/neofetch/issues/28) opened a bug report on the repo requesting "ascii art support". \[1\] I jumped on this and was shocked to see how easy it was to implement, I had a working version the same day and it was in master a day later. 

As I kept working on Neofetch everyday, looking for ways to improve it I decided to get it to get it to feature parity with Screenfetch. Once Neofetch supported displaying the same info as Screenfetch I thought to myself, what else can we add to Neofetch?

I started adding new info functions, features, config options and Neofetch now supported displaying info like Current Terminal Emulator, Terminal Emulator Font, Device Model (Name of laptop, etc) and much more.

I'm still working on Neofetch everyday and I'm still looking for ways to extend it further. :-)

\[1\] https://github.com/dylanaraps/neofetch/issues/28


## How does Neofetch differ from Screenfetch?