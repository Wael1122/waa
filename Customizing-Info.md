As of commit [9daacdd](https://github.com/dylanaraps/fetch/commit/9daacddda1d0adca9df1ff8e9aad13d974c09314) the info array at the top of the script has changed to a regular function. The benefits of this are pretty cool, you can now use **any** bash syntax to customize what gets displayed. You could have an if statment and only print window manager and gtk themes if X is running or only show current song if there's one playing.

Here's what the function looks like, it's very similar to the array we had before.

```sh
printinfo () {
    info title
    info underline

    info "OS" distro
    info "Kernel" kernel
    info "Uptime" uptime
    info "Packages" packages
    info "Shell" shell
    info "Window Manager" windowmanager
    info "GTK Theme" gtktheme
    info "Icons" gtkicons
    info "CPU" cpu
    info "Memory" memory

    info linebreak
    info cols
}
```

## Adding Custom Info

The script comes with two helper functions that make it easier to display more info.

#### info

```sh
Usage: info "subtitle" function

# Print Memory
info "Memory" memory

# Print Uptime and color the subtitle Orange
info "$(color 5)Uptime" uptime

```

#### prin

You can also just use `printf` or `echo -e` but you'll have to format/color<br \>
the text yourself.

```sh
Usage: prin "Custom message" or "Subtitle: Custom message"

# Print a custom message
prin "They call me Stacy"

# Print a custom info line
prin "Date: $(date)"

# Print a custom message and color it blue
prin "$(color 4)That's not my name"

```

## More complex examples

#### Only show window manager and gtk themes if X is running.

```sh
printinfo () {
    info title
    info underline
    
    # ...

    if [ "$DISPLAY" ]; then
        info "Window Manager" windowmanager
        info "GTK Theme" gtktheme
        info "Icons" gtkicons
    fi

    # ...
}
```

#### Only show GTK theme if there's one in use

```sh
printinfo () {
    info title
    info underline
    
    # ...

    getgtktheme
    if [ "$gtktheme" != "None" ]; then
        prin "GTK Theme: $gtktheme"
        info "Icons" gtkicons
    fi

    # ...
}
```