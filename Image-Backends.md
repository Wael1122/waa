Neofetch 3.0 included a rewrite of how we handles different modes (`image`, `ascii` and etc) which allowed us to add 3 additional image backends to Neofetch. Neofetch now supports displaying images using [`catimg`](https://github.com/posva/catimg), [`libcaca`](http://caca.zoy.org/wiki/libcaca) and [`jp2a`](https://csl.name/jp2a/).


## Image Backends

Note: The screenshot for `iterm2`, `tycat` and `w3m` is the same since the output in these backends is identical. I also can't get a screenshot of `iterm2` since I don't have a macOS machine. 

### Ascii

```sh
# Usage: neofetch --ascii 
#        neofetch --ascii /path/to/ascii
```

![ascii](http://i.imgur.com/pHU40xh.png)


### Caca

```sh
# Usage: neofetch --caca 
#        neofetch --caca /path/to/img
#        neofetch --caca /path/to/dir/
```

![caca](http://i.imgur.com/SBDQgxx.png)


### Catimg

```sh
# Usage: neofetch --catimg 
#        neofetch --catimg /path/to/img
#        neofetch --catimg /path/to/dir/
```

![catimg](http://i.imgur.com/qOcCNxU.png)


### iTerm2

```sh
# Usage: neofetch --iterm2 
#        neofetch --iterm2 /path/to/img
#        neofetch --iterm2 /path/to/dir/
```

![iterm2](http://i.imgur.com/ys5R5cu.png)

### Jp2a

```sh
# Usage: neofetch --jp2a 
#        neofetch --jp2a /path/to/img
#        neofetch --jp2a /path/to/dir/
```

![jp2a](http://i.imgur.com/d5jVIGY.png)


### Tycat

```sh
# Usage: neofetch --tycat 
#        neofetch --tycat /path/to/img
#        neofetch --tycat /path/to/dir/
```

![tycat](http://i.imgur.com/ys5R5cu.png)

### W3m

```sh
# Usage: neofetch --tycat 
#        neofetch --tycat /path/to/img
#        neofetch --tycat /path/to/dir/
```

![w3m](http://i.imgur.com/ys5R5cu.png)

### Off

```sh
# Usage: neofetch --off
```

![off](http://i.imgur.com/7hzZrJi.png)