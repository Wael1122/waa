There are a ton of options and launch flags in the script that allow you<br \>
to customize just about everything. This wiki page explains each option<br \>
in detail so you have a better understanding of how they work.

This page may be outdated, see the comments inside the script for the<br \>
most recent changes.

## Info:

#### speed_type 

Change which CPU speed type is displayed.

Possible values: `current`, `min`, `max`, `bios`, `scaling_current`,<br \>
`scaling_min`, `scaling_max.`

**NOTE**: This only support Linux with cpufreq.


#### uptime_shorthand

Shorten the output of uptime.

Possible values: `tiny`, `on`, `off`


#### gpu_shorthand

Shorten the output of GPU.

Possible values: `on`, `off`


#### gtk_shorthand

Shorten the output of GTK themes and icons.

Possible values: `on`, `off`


#### gtk2

When set to `off` GTK2 themes and icons will be hidden from the output<br \>
of GTK. 

Possible values: `on`, `off`


#### gtk3

When set to `off` GTK3 themes and icons will be hidden from the output<br \>
of GTK. 

Possible values: `on`, `off`


## Text Colors:


#### colors

A shorthand way of coloring the text. The numbers color in this<br \>
order: `title`, `@`, `subtitle`, `colon`, `underline`, `info`

Example usage: `--colors 1 2 3 4 5 6`

Possible values: any `numbers` up to 6 times

**Note:** If you use just want to color the first 3 values then<br \>
it'll look like this: `--colors 1 2 3`. When you use less than <br \>
6 colors the empty values use their defaults.


#### title_color

Change the color of the title at the top of the output.

Possible values: `number`


#### at_color

Change the color of the `@` symbol in the title at the top of<br \>
the output.

Possible values: `number`


#### subtitle_color

Change the color of the subtitles.

Possible values: `number`


#### colon_color

Change the color of the subtitle's colon.

Possible values: `number`


#### underline_color

Change the color of the underline under the title.

Possible values: `number`


#### info_color

Change the color of the info.

Possible values: `number`


## Text Formatting


#### underline

Enable/Disable the underline at the top of the script.

Possible values: `on`, 'off'


#### underline_char

Character to create the underline with.

Possible values: Any single character


#### line_wrap

Enable/Disable line wrap. When set to `off` long lines just go<br \>
offscreen

Possible values: `on`, `off`


#### bold

Enable/Disable bold text.

Possible values: `on`, `off`


#### prompt_height

Set this value to the amount of lines your terminal prompt<br \>
takes up. This fixes the script output getting cut off when the<br \>
prompt height was too high.

Possible values: `number`


## Color Blocks


#### color_blocks

Enable/Disable the color palette that gets printed beneath<br \>
the info.

Possible values: `on`, `off`


#### block_width

How many space chars wide to make each color block.

Possible values: `number`


#### block_range

The range of colors to print. To print 16 colors use<br \>
the value `--block_range 0 15`

Possible values: `number number`


## Image


#### image

Image source, where we get the image from.

Possible values: `wall`, `shuffle`, `/path/to/img.png`, `off`


#### image_backend

Which program to use to display images.

Possible values: `w3m`, `iterm2`


#### shuffledir

Directory to shuffle through when `image=shuffle`.

Possible values: `directory`


#### font_width

This is used to dynamically size the image and must be<br \>
set to your font width for it to be sized correctly. If you <br \>
don't know your font width just keep trying values until the<br \>
image takes up **half** the terminal width.

Possible values: `number`


#### image_position

Which side of the terminal to draw the image on.

Possible values: `left`, `right`


#### split_size

How big the image and text splits should be. The default value<br \>
of `2` makes the image and text take up **half** the terminal each.<br \>
A value of `3` will make the image and text take up a **third** of the<br \>
terminal each and etc.

Possible values: `number`


#### crop_mode

Which crop mode to use.

Possible values: `normal`, `fit`, `fill`

**Note**: For more info on `fit` and `fill`, see this wiki page:

https://github.com/dylanaraps/fetch/wiki/What-is-Smart-Crop%3F


#### crop_offset

Change the crop offset for `normal` crop_mode.

Possible values: `northwest`, `north`, `northeast`, `west`, `center`,<br \>
`east`, `southwest`, `south`, `southeast`


#### xoffset

How many pixels to pad the image on the left.

Possible values: `number`

**Note**: This only works with `image_backend` `w3m`.


#### yoffset

How many pixels to pad the image from the top.

Possible values: `number`

**Note**: This only works with `image_backend` `w3m`.


#### gap

Gap between images and text. The value is the amount of<br \>
space chars to pad the text.

Possible values: `number`, `-number`

**Note**: This can also take a negative value which will<br \>
push the text closer to the left.


#### clean

Remove all cropped images.

Possible values: `none`


## Screenshot:


#### scrot

Take a screenshot on script end.

Possible values: '/path/to/save/scrot.png`

**Note**: An empty value will save the screenshots in `scrot_dir`/`scrot_name`.


#### scrot_cmd

Screenshot program to launch.

Possible values: `program name`
