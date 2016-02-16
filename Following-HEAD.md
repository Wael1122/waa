This page is here to inform people using the master branch
of any breaking changes to config files.

### 17/02/2016

- `wmctrl` is now a required dependency on Linux / BSD. See **[#75](https://github.com/dylanaraps/fetch/issues/75)** <br \>for my reasoning
for doing this.
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
