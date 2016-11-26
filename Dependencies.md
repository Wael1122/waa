This page lists the programs/dependencies neofetch needs to run.

## Table of Contents

- **[Required dependencies](#required-dependencies)**
- **[Image mode dependencies](#image-mode-dependencies)**
- **[Optional dependencies](#optional-dependencies)**
    - [Song](#song)
    - [Desktop Environment and Window Manager](#desktop-environment-and-window-manager)
    - [Wallpaper](#wallpaper)
    - [Resolution](#resolution)
    - [Screenshot](#screenshot)
    - [GPU](#gpu)
- **[iOS dependencies](#ios)**
- **[Android dependencies](#android)**


## Required dependencies:

- `Bash 3.0+`
    - Alpine Linux: You also need `ncurses`.


## Image mode dependencies:

These dependencies are required for image mode to work.

- Displaying images: `w3m-img` \[1\] or `iTerm2` or `Terminology` \[2\]
- Thumbnail creation: `imagemagick`
- Window size: A terminal emulator that supports `\033[14t` \[3\] or `xdotool` or `xwininfo + xprop` or `xwininfo + xdpyinfo`

\[1\] `w3m-img` is sometimes bundled together with `w3m`.

\[2\] Image support is built into Terminology and iTerm2, and doesn't require w3m-img.

\[3\] See this wiki page to find out if your terminal emulator supports `\033[14t` or if you need an additonal dependency.


## Optional dependencies:

### Song

- Google Play Music Desktop Player: [`gpmdp-remote`](https://github.com/iAndrewT/gpmdp-remote)
- MPD: `mpc`
- CMUS
- MOC
- Spotify
- Rhythmbox
- Banshee
- Amarok
- Deadbeef
- GNOME Music
- Lollypop

### Desktop Environment and Window Manager

- Desktop Environment and Window Manager: `xprop`

### Wallpaper

**Linux, BSD and Solaris**

- Wallpaper: `feh`, `nitrogen` or `gsettings`

**Windows and macOS**

- No additional dependencies needed.

### Resolution

**Linux, BSD and Solaris**

- Resolution: `xorg-xrandr` or `xorg-xdpyinfo` \[1\]

**macOS**

- Resolution (quicker): `screenresolution` \[2\]

\[1\] Xrandr is prefered over xdpyinfo as Xrandr supports multi monitor and refresh rate display in the output.

\[2\] `screenresolution` is installed for you when using homebrew.

### Screenshot

- Screenshot: `scrot` \[1\]

\[1\] You can use the launch flag `--scrot_cmd` or change the config option `$scrot_cmd` to your screenshot program's cmd and neofetch will use it instead of scrot.

### GPU

**BSD and Solaris**

- GPU: `glxinfo`
    - Not required on FreeBSD.


### iOS

These dependencies can all be installed through Cydia.<br \>
Note: The cydia package installs these dependencies for you.

- `Bourne-Again SHell`
- `Core Utilities`
- `Core Utilities (/bin)`
- `Darwin Tools`
- `system-cmds`
- `Gawk`
- `grep`


### Android

- `bash`
- `busybox`

**Note:** I recommend installing `termux` from the Play Store or F-Droid. Termux provides you with a fully working Linux environment, doesn't require root acess and includes all dependencies.

**Note:** Neofetch is in Termux's official repos.

