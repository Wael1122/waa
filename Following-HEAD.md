This page is here to inform people using the master branch
of any breaking changes to config files.

### 1.4

- Fetch has been renamed to `Neofetch`.

### 1.3
Removed `$*_color` variables/flags in favour of a general `$colors`<br \>
variable/flag. See my writeup here: **https://github.com/dylanaraps/fetch/pull/96**

- You no longer need to set `font_width`, fetch does it automatically.<br \>
- `image_size=half` was renamed to `image_size=auto`.
- `gnu screen`, `st` and `konsole` no longer work with `w3m-img` mode. See **[#82](https://github.com/dylanaraps/fetch/pull/82#issuecomment-185973761)**
- Removed `--stdout_separator` (Separator is now 2 spaces)
- Removed `--stdout_subtitles`
- Removed `--stdout_title`

**Windows**
- `getvisualstyle` has been merged with `getstyle`. Make the following change:

```sh
# The title inside the quotes can be
# whatever you like.

# Old
info "Visual Style" visualstyle

# New
info "Theme" theme
```

### 1.2

- `xprop` is now a required dependency. See **[#79](https://github.com/dylanaraps/fetch/issues/79)** <br \>for my reasoning for doing this.
- `windowmanager` was renamed to `wm` so you'll need to update your printinfo<br \>
function in your config file.
- Dropped the `gtk` from these printinfo functions `gtktheme`, `gtkicons`<br \>
and `gtkfont`. Theme output will be blank until you make these changes:

```sh
# Old Naming
info "GTK Theme" gtktheme
info "Icons" gtkicons
info "Font" gtkfont

# New Naming
info "Theme" theme
info "Icons" icons
info "Font" font
```
