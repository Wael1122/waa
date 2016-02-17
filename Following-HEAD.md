This page is here to inform people using the master branch
of any breaking changes to config files.

### 17/02/2016

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
