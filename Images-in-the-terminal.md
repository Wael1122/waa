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
| Gnome-terminal    | Yes     | Yes        |
| iTerm             | N/A     | Yes        | See \[1\] |
| konsole           | Yes     | No         |
| st                | Yes     | No         | Image disappears on window focus and resize |
| Terminator        | Yes     | Yes        | Image disappears on window focus and resize |
| Terminology       | N/A     | `\033}qs\000` | See \[2\] |
| Termite           | Yes     | Yes        |
| tilda             | No      | Yes        |
| URxvt             | Yes     | Yes        | Display problems with xft fonts  |
| Xfce4-terminal    | Yes     | Yes        |
| Xterm             | Yes     | Yes        |

\[1\] iTerm doesn't require `w3m-img` to display images. Instead it uses a<br \>
set of escape sequences built into iTerm.

\[2\] Terminology doesn't require `w3m-img` to display images. Instead it uses<br\> 
a builtin program called `tycat`.

Note: For image mode to work, both columns need to be `Yes`.

Yes  
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


## Customization

Neofetch has various flags/options that let you customize the image output. 

#### Options

| Option Name | Launch Flag | Config Option | Args | Notes |
| ----------- | ----------- | ------------- | ---- | ----- |
| Source      | --image     | image         | `wall` `ascii` `/path/to/img` `/path/to/dir/` `off` | If an invalid image mode is specified neofetch will fallback to ascii mode. |
| Size        | --size      | image_size    | `auto` `00px` `00%` `none` | 
| Position    | --image_position | image_position | `left` `right` | Doesn't work with iTerm2 and Terminology
| Crop Mode   | --crop_mode | crop_mode     | `normal` `fit` `fill` | See this wiki page for more info. [What is waifu crop?](https://github.com/dylanaraps/neofetch/wiki/What-is-Waifu-Crop%3F#)
| Crop Offset | --crop_offset | crop_offset | `northwest` `north` `northeast` `west` `center` `east` `southwest` `south` `southeast` | How this works: [crop_gravity](http://www.imagemagick.org/Usage/crop/#crop_gravity)
| X offset    | --xoffset     | xoffset     | `num` | Doesn't work with iTerm2 and Terminology
| Y offset    | --yoffset     | yoffset     | `num` | Doesn't work with iTerm2 and Terminology
| Gap         | --gap         | gap         | `num` | Gap between image and text
| Clean       | --clean       | N/A         | N/A   | Remove all cropped images