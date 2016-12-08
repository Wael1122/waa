This wiki page lists all of the [shellcheck](https://www.shellcheck.net/) errors that we're ignoring when testing Neofetch.


### [SC1090](https://github.com/koalaman/shellcheck/wiki/SC1090)

> Can't follow non-constant source. Use a directive to specify location.

This error has been disabled since we're not sourcing the config file when running shellcheck.


### [SC2009](https://github.com/koalaman/shellcheck/wiki/SC2009)

> SC2009 Consider using pgrep instead of grepping ps output.

We were originally using `pgrep` until we found out that `pgrep` has some issues on macOS systems.


### [SC2034](https://github.com/koalaman/shellcheck/wiki/SC2034)

> foo appears unused. Verify it or export it.

This error has been disabled since we dynamically use the info variables. (`$kernel`)


### [SC2153](https://github.com/koalaman/shellcheck/wiki/SC2153)

> Possible Misspelling: MYVARIABLE may not be assigned, but MY_VARIABLE is.

We use a lot of Environment Variables and this error comes up whenever we reassign an Environment Variable to a local variable. Totally harmless.


### [SC2154](https://github.com/koalaman/shellcheck/wiki/SC2154)

> var is referenced but not assigned.

This error has been disabled since the variables are in the config files which we don't source when testing with shellcheck.


### [SC2178](https://github.com/koalaman/shellcheck/wiki/SC2178)

> Variable was used as an array but is now assigned a string.

Each info function in Neofetch is split into separate parts for each Operating System. One OS might need an array to get the info and the others may not. Shellcheck sees mixed usage of Arrays/Variables and that's what causes this error. 

