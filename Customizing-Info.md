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
    info "Resolution" resolution
    info "DE" de
    info "WM" wm
    info "WM Theme" wmtheme
    info "Theme" theme
    info "Icons" icons
    info "CPU" cpu
    info "GPU" gpu
    info "Memory" memory

    # info "Font" font
    # info "Disk" disk
    # info "Battery" battery
    # info "Song" song
    # info "Local IP" localip
    # info "Public IP" publicip
    # info "Users" users
    # info "Birthday" birthday

    info linebreak
    info cols
    info linebreak
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

#### prin

You can also just use `printf` or `echo -e` but you'll have to format/color<br \>
the text yourself.

```sh
Usage: prin "Custom message" or "Subtitle" "Custom message"

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
printinfo () {
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

    info linebreak
    info cols

    # Wait for the functions to complete
    wait
}
```