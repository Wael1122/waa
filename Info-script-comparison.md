How does Neofetch differ from X?

This question comes up quite a lot when I post update threads and this wiki page<br \>
aims to answer this. Neofetch is different in a lot of ways and I'm going to try<br \>
and summarize them below. If I've missed anything, let me know and I'll add it to<br \>
the list.

**NOTE**: These comparisons below apply to both Screenfetch and Archey3

| Program     | Distro Ascii | Images | Language | License | Single File | In Active Development? | 
| -------     | ------------ | ------ | -------- | ------- | ----------- | ---------------------- | 
| Neofetch    | Yes          | Yes    | Bash 3   | MIT     | No          | Yes                    |
| Screenfetch | Yes          | No     | Bash 4   | GPLv3   | Yes         | Yes                    |
| Archey3     | Yes          | No     | Python 3 | GPL     | Yes         | No                     |


## General

**Neofetch supports bash 3.0+**<br \>
Screenfetch requires at least bash 4.0 to be installed.

**Neofetch is more actively developed.**<br \>
I'm working on Neofetch almost everyday whereas ~~Screenfetch~~ and Archey haven't been updated
in months. 

**Neofetch is faster.**<br \>
Neofetch heavily uses bash builtins and we only spawning external processes <br \>
when necessary. 

**Neofetch is more customizable.**<br \>
There are config options to customize almost everything, see the default config<br \>
for all of the options and what they do.

https://github.com/dylanaraps/neofetch/blob/master/config/config

Neofetch allows you to customize what info gets displayed using bash syntax, see <br \>
this wiki page which explains how this works.

https://github.com/dylanaraps/neofetch/wiki/Customizing-Info

## Images

**Neofetch supports displaying a full color image next to the info.**<br \>
Using `w3m-img`, `Terminology` or `iTerm2` neofetch can display an image<br \>
of your choice, your current wallpaper or even shuffle through a directory<br \> 
of images.

The image is dynamically sized based on your font width and window size.

**Neofetch supports displaying custom ascii art from a file.**<br \>
Neofetch can display any ascii art from a file next to the info!

**Neofetch stores all of the ascii art is in seperate files**<br \> 
I'm storing the ascii art as seperate files instead of taking up a huge amount<br \>
of space inside the script.

## Info

**Neofetch has a more stylized output**<br \>
Neofetch aims to have a prettier and more configurable output, almost every info<br \>
function has config options to customize the output.

**Neofetch can display much more info than the other tools**<br \>
Neofetch can display the following information:

`Distro` `Kernel` `Uptime` `Packages` `Shell` `Resolution`<br\>
`Desktop Environment` `Window Manager` `Window Manager Theme`<br \>
`System Theme` `System Icons` `CPU` `GPU` `Memory`<br \>
`System Font` `Disk` `Battery` `Current Song` `Local IP`<br \>
`Public IP` `Users` `Birthday`

**Neofetch can display a progress bar next to certain info**<br \>
Neofetch can show a progress bar next to the following info:

`CPU Usage` `Memory` `Disk` `Battery`
