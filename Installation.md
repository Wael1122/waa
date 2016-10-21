<!-- Dependencies {{{ -->

## Table of contents

- [Dependencies]()
    - [Required dependencies]()
    - [Image mode dependencies]()
    - [Optional dependencies]()
        - [Song]()
        - [Wallpaper]()
        - [Resolution]()
        - [Screenshot]()
        - [GPU]()
        - [Desktop Environment and Window Manager]()
- [iOS dependencies]()### 

## Dependencies

### Required dependencies:

- `Bash 3.0+`
    - Alpine Linux: You also need `ncurses`.


### Image mode dependencies:

These dependencies are required for image mode to work.

- Displaying images: `w3m-img` \[1\] or `iTerm2` or `Terminology` \[2\]
- Thumbnail creation: `imagemagick`
- Window size: A terminal emulator that supports `\033[14t` \[3\] or `xdotool` or `xwininfo + xprop` or `xwininfo + xdpyinfo`

\[1\] `w3m-img` is sometimes bundled together with `w3m`.

\[2\] Image support is built into Terminology and iTerm2, and doesn't require w3m-img.

\[3\] See this wiki page to find out if your terminal emulator supports `\033[14t` or if you need an additonal dependency.


### Optional dependencies:

#### Song

- Google Play Music Desktop Player: [`gpmdp-remote`](https://github.com/iAndrewT/gpmdp-remote)
- MPD: `mpc`
- CMUS: `cmus
- MOC: `moc`
- Spotify: `spotify`

#### Desktop Environment and Window Manager

- Desktop Environment and Window Manager: `xprop` \[1\]


#### Wallpaper

#### Resolution

#### Screenshot

- Displaying song information from Google Play Music Desktop Player: [`gpmdp-remote`](https://github.com/iAndrewT/gpmdp-remote)


##### Linux / BSD / Solaris

- Wallpaper: `feh`, `nitrogen` or `gsettings`

- Resolution: `xorg-xrandr` or `xorg-xdpyinfo` \[2\]
- Screenshot: `scrot` \[3\]

##### OSX

- Resolution (quicker): `screenresolution`

##### BSD / Solaris

- GPU: `glxinfo`
    - Not required on FreeBSD.




\[2\] Xrandr is prefered over xdpyinfo as Xrandr supports multi monitor and refresh rate display in the<br \>
output.

\[3\] You can use the launch flag `--scrot_cmd` or change the config option `$scrot_cmd` to your screenshot<br \>
program's cmd and neofetch will use it instead of scrot.


##### iOS

These dependencies can all be installed through Cydia.<br \>
Note: The cydia package installs these dependencies for you.

- `Bourne-Again SHell`
- `Core Utilities`
- `Core Utilities (/bin)`
- `Darwin Tools`
- `system-cmds`
- `Gawk`
- `grep`


<!-- }}} -->