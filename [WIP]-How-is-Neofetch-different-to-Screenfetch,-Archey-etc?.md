This question comes up quite a lot when I post update threads and this wiki page<br \>
aims to answer this. Neofetch is different in a lot of ways and I'm going to try<br \>
and summarize them below. If I've missed anything, let me know and I'll add it to<br \>
the list.

**NOTE**: These comparisons below apply to both Screenfetch and Archey3

| Program     | Distro Ascii | Images | License | In Active Development? | 
| -------     | ------------ | ------ | ------- | ---------------------- | 
| Neofetch    | Yes          | Yes    | MIT     | Yes
| Screenfetch | Yes          | No     | GPLv3   | No
| Archey3     | Yes          | No     | GPL     | No


## General

**Neoetch supports bash 3.0+**<br \>
Screenfetch requires at least bash 4.0 to be installed.

**Neofetch is more actively developed.**<br \>
I'm working on Neofetch almost everyday whereas Screenfetch and Archey haven't been updated
in months. 

**Neofetch is faster.**<br \>
We're heavily using bash builtins and we're only spawning external processes <br \>
when necessary. 

**Neofetch is more customizable.**<br \>
There are config options to customize almost everything, see the default config<br \>
for all of the options and what they do.

https://github.com/dylanaraps/neofetch/blob/master/config/config

Neofetch allows you to customize what info gets displayed using bash syntax, see <br \>
this wiki page which explains how this works.

https://github.com/dylanaraps/neofetch/wiki/Customizing-Info

## Images

**Neoetch supports displaying a full color image next to the info.**<br \>
Using `w3m-img` or `iTerm2` neofetch can display an image of your choice, your<br \>
current wallpaper or even shuffle through a directory of images.

The image is dynamically sized based on your font width and window size.

**Neofetch supports displaying custom ascii art from a file.**<br \>
Neofetch can display any ascii art from a file next to the info!

**Neofetch stores all of the ascii art is in seperate files**<br \> 
We're storing the ascii art as seperate files instead of taking up a huge amount<br \>
of space inside the script.

## Info

**Neofetch has a more stylized output**<br \>
Neofetch aims to have a prettier and more configurable output, almost every info<br \>
function has config options to customize the output.


