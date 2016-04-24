I get a lot of comments/questions about how to get w3m-img mode working with<br \>
neofetch. This wiki page will guide you through setting up neofetch/w3m-img and<br \>
will try to explain the various quirks of this mode.


## Requirements


#### Dependencies

- `w3m-img`
    - Image rendering in the terminal.
    - This is sometimes bundled together with `w3m`.

- `imagemagick`
    - Generating thumbnails and cropping the images.


#### Terminal Emulator

Image mode requires a terminal emulator that plays nicely with w3m-img and<br \>
supports the following escape sequence.

- `\033[14t`
    - Prints terminal window size in pixels.
    - Used to dynamically size the images.
    - Used to dynamically pad the text.

The table below lists my testing of various terminal emulators, what works and<br \>
what doesn't.

| Terminal Emulator | w3m-img | `\033[14t` | Quirks |
| ----------------- | ------- | ---------- | ------ |
| URxvt             | Yes     | Yes        | Display problems with xft fonts  |
| Xterm             | Yes     | Yes        |
| Xfce4-terminal    | Yes     | Yes        |
| Termite           | Yes     | Yes        |
| Terminator        | Yes     | Yes        | Image disappears on window focus and resize |
| st                | Yes     | No         | Image disappears on window focus and resize |
| tilda             | No      | Yes        |

Note: For image mode to work, both columns need to be `Yes`.


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
