Note: This page is unfinished.

I first started writing Neofetch or as it was originally called "fetch" back in November of 2015. I was just getting started with shell scripting at this point so I was writing scripts for anything and everything I could think of. I had the idea of showing an image next to system info and decided to turn it into a working script.

The screenshot below is of the oldest version of `fetch`. This version only properly worked on Arch systems, had no support for ascii logos and everything was hardcoded. The script was only `60` lines long and was only meant to work on my machine at the time. 

Here's the script source: [fetch - nov 10 2015](https://github.com/dylanaraps/dotfiles/blob/0a146c986b1540949146f753998ba91a414fd716/scripts/fetch.sh)

![Oldest screenshot of fetch](https://u.teknik.io/h7KSz.png)
<br \><sub>Oldest screenshot of `fetch`</sub>

I decided to keep working on the script everyday, fixing bugs and adding features. During this period I kept getting comments and messages from people asking to add support for their Operating System or Distro. I started adding support for other operating systems and I realized that to cleanly add support for more operating systems I would have to rewrite the script from scratch. 

And so I did. I spent the entire weekend writing the script from scratch, only this time it was written with multi-OS support in mind. After the rewrite the script went from 100~ to 740~ lines of code. The script now had command line flags, config options and supported Mac OS, Windows and a ton of Linux distros.


![First standalone version](https://u.teknik.io/IX209.png)
<br \><sub>First standalone version of `fetch`</sub>

### TODO