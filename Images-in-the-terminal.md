I get a lot of comments/questions about how to get w3m-img mode working with<br \>
neofetch. This wiki page will guide you through setting up neofetch/w3m-img and<br \>
will try to explain the various quirks of this mode.


## Requirements


#### Dependencies

- `w3m-img`
    - Image rendering in the terminal.
    - This is sometimes bundled together with `w3m`.
    - `Terminology` and `iTerm` users don't need to install w3m-img.

- `imagemagick`
    - Generating thumbnails and cropping the images.

- A terminal emulator that supports `\033[14t` or `xdotool` or<br \>
`xwininfo + xprop` or `xwininfo + xdpyinfo`
    - Getting the terminal window size in pixels so that we can size the image correctly.

#### Terminal Emulator

The table below lists my testing of various terminal emulators, what works and<br \>
what doesn't.

| Terminal Emulator | w3m-img | Quirks |
| ----------------- | ------- | ------ |
| Gnome-terminal    | Yes     | - Image disappears on window focus and resize<br\>- Possible issues on Fedora, see #295
| iTerm             | N/A     | See \[1\] |
| konsole           | Yes     |
| st                | Yes     | Image disappears on window focus and resize |
| Terminator        | Yes     | Image disappears on window focus and resize |
| Terminology       | N/A     | See \[2\] |
| Termite           | Yes     |
| tilda             | No      |
| URxvt             | Yes     | ~~Display problems with xft fonts~~ Fixed! See: [Changelog](https://github.com/dylanaraps/neofetch/blob/a699c430de6dacb38a55f851157a226a9d470078/Changelog.md#images)   |
| Xfce4-terminal    | Yes     |
| Xterm             | Yes     |

\[1\] iTerm doesn't require `w3m-img` to display images. Instead it uses a<br \>
set of escape sequences built into iTerm.

\[2\] Terminology doesn't require `w3m-img` to display images. Instead it uses<br\> 
a builtin program called `tycat`.

Note: For image mode to work, the `w3m-img` column must say `yes` and you must have<br \>
the dependencies installed.

## Image source

Neofetch by default will try to use your current wallpaper as the image. If the<br \>
wallpaper detection fails we fallback to ascii mode, when ths happens you should<br \>
try and launch neofetch with `--image path/to/image` or `--image path/to/dir/`.

The list below shows the current wallpaper setters we support.

**Linux / BSD**

- feh
- nitrogren
- gsettings

**Mac OS X / Windows**

- Builtin wallpaper setter

If your wallpaper setter isn't listed here and there's an easy way to find where<br \>
the current wallpaper is stored, open an issue and I'll gladly add support for
it.


## Usage

Once you've installed `w3m-img`, `imagemagick`, have a terminal emulator that<br \>
meets the criteria above and have a working image source, neofetch should<br \>
display images correctly.

If neofetch still won't display the images then you should open a new issue on<br \>
github and provide me with a verbose log.
