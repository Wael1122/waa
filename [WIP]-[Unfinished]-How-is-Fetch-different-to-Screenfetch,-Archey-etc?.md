This question comes up quite a lot when I post update threads and this wiki page<br \>
aims to answer this. Fetch is different in a lot of ways and I'm going to try<br \>
and summarize them below. If I've missed anything, let me know and I'll add it<br \>
below.

**NOTE**: These comparisons below apply to both Screenfetch and Archey3

## General

**Fetch supports bash 3.0+**
Screenfetch requires at least bash 4.0 to be installed.

**Fetch is more actively developed.**<br \>
I'm working on fetch everyday whereas Screenfetch and Archey haven't been updated<br \> 
in months. 

**Fetch is faster.**<br \>
We're heavily using bash builtins and we're only spawning external processes <br \>
when necessary. 

This makes us stupid fast.

**Fetch is more customizable.**<br \>
There are config options to customize almost everything, see the default config<br \>
for all of the options and what they do.

https://github.com/dylanaraps/fetch/blob/master/config/config

Fetch allows you to customize what info gets displayed using bash syntax, see <br \>
this wiki page which explains how this works.

https://github.com/dylanaraps/fetch/wiki/Customizing-Info

## Images

**Fetch supports displaying a full color image next to the info.**<br \>
Using `w3m-img` or `iTerm2` fetch can display an image of your choice, your<br \>
current wallpaper or even shuffle through a directory of images.

The image is dynamically sized based on your font width and window size.

**Fetch supports displaying custom ascii art from a file.**<br \>
Fetch can display any ascii art from a file next to the info!


**Fetch stores all of the ascii art is in seperate files**<br \> 
We're storing the ascii art as seperate files instead of taking up a huge amount<br \>
of space inside the script.

## Info

**Fetch has a more stylized output**<br \>
Fetch aims to have a prettier and more configurable output, almost every info<br \>
function has config options to customize the output.


