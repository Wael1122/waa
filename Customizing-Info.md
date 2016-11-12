As of commit [9daacdd](https://github.com/dylanaraps/fetch/commit/9daacddda1d0adca9df1ff8e9aad13d974c09314) the info array at the top of the script has changed to a regular function. The benefits of this are pretty cool, you can now use **any** bash syntax to customize what gets displayed. This makes it really easy to add your own custom info to neofetch.

Here's what the function looks like, it's very similar to the array we had before.

```sh
printinfo () {
    info title
    info underline

    info "Model" model
    info "OS" distro
    info "Kernel" kernel
    info "Uptime" uptime
    info "Packages" packages
    info "Shell" shell
    info "Resolution" resolution
    info "DE" de
    info "WM" wm
    info "WM Theme" wm_theme
    info "Theme" theme
    info "Icons" icons
    info "Terminal" term
    info "Terminal Font" term_font
    info "CPU" cpu
    info "GPU" gpu
    info "Memory" memory

    # info "CPU Usage" cpu_usage
    # info "Disk" disk
    # info "Battery" battery
    # info "Font" font
    # info "Song" song
    # info "Local IP" local_ip
    # info "Public IP" public_ip
    # info "Users" users
    # info "Birthday" birthday

    info linebreak
    info cols
    info linebreak
}

```

## Adding Custom Info

The script comes with two helper functions that make it easier to display more info.

#### info

```sh
Usage: info "subtitle" function

# Print Memory
info "Memory" memory
```

Full list of functions:

`distro` `kernel` `uptime` `packages` `shell` `resolution`<br\>
`de` `wm` `wmtheme` `theme` `icons` `cpu` `gpu` `memory`<br \>
`font` `disk` `battery` `song` `local_ip` `public_ip` `users`<br \>
`birthday` `term` `term_font`  `cpu_usage`

#### prin

You can also just use `printf` or `echo -e` but you'll have to format/color<br \>
the text yourself.

```sh
Usage: prin "Custom message" or prin "Subtitle" "Custom message"

# Print a custom message
prin "They call me Stacy"

# Print a custom info line
prin "Date" "$(date)"

# Print a custom message and color it blue
prin "$(color 4)That's not my name"

```

## More complex examples

#### Speed up the script by running the functions asynchronously

You can make the script 2x faster by gathering the info asynchronously, the only caveat is that the order that all of the info is printed in will be based on what completes first. You can add this to your printinfo function by adding an `&` sign to the info lines you want to be asynchronous then by adding a single `wait` to the bottom of the function.

```sh
print_info () {
    # Lines without an '&' sign will be displayed in 
    # the order they appear here.
    info title
    info underline

    info "OS" distro &
    info "Kernel" kernel &
    info "Uptime" uptime &
    info "Packages" packages &
    info "Shell" shell &
    info "Window Manager" windowmanager &
    info "GTK Theme" gtktheme &
    info "Icons" gtkicons &
    info "CPU" cpu &
    info "GPU" gpu &
    info "Memory" memory &

    info line_break
    info cols
    info line_break

    # Wait for the functions to complete
    wait
}
```