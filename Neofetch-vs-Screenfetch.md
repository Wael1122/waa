**NOTE:** This page is a wip

The goal of this wiki page is to answer these questions:

- How is Neofetch different from Screenfetch?
- What's wrong with Screenfetch?

## Table of Contents

- [Why was Neofetch created?](#why-was-neofetch-created)
- [The problem with Screenfetch](#the-problem-with-screenfetch)
- [How does Neofetch differ from Screenfetch](#how-does-neofetch-differ-from-screenfetch)

## Why was Neofetch created?

Neofetch or as it was originally called `fetch` was never meant to be a replacement for Screenfetch nor was it ever meant to display Ascii logos. Neofetch first started as my `70` line hardcoded script that only supported Arch Linux, only displayed a tiny amount of info and only supported showing images with w3m-img. 

I started posting screenshots of my system to [/r/unixporn/](https://reddit.com/r/unixporn) which included my tiny little script. People started using the script and started asking me to add support for their Linux Distros and later their Operating systems. Me being happy that anyone is using something that I created started adding support various Distros and Operating systems. 

![Oldest screenshot of fetch](https://u.teknik.io/h7KSz.png)
<br \><sub>Oldest screenshot of `fetch`</sub>

When it got to adding support for Mac OS I realized that I had hit a stopping point. The script wasn't written in a way that would allow me to easily expand it to more Operating systems, it needed a rewrite. So I rewrote the script from scratch over an entire weekend and the result is the script base/structure that neofetch is still using today.

I continued to work on Neofetch everyday and whenever someone would suggest a feature, I would add it no questions asked. One day a user by the name of [@aloisdg](https://github.com/dylanaraps/neofetch/issues/28) opened a bug report on the repo requesting "ascii art support". \[1\] I jumped on this and was shocked to see how easy it was to implement, I had a working version the same day and it was in master a day later. 

![early distro ascii support](https://camo.githubusercontent.com/92b2d32b4f1d22b6fb2dbb680417c8a91a5b8f3b/687474703a2f2f692e696d6775722e636f6d2f744746664b4b302e706e67)
<br \><sub>Early distro ascii support</sub>

As I kept working on Neofetch everyday, looking for ways to improve it I decided to get it to get it to feature parity with Screenfetch. Once Neofetch supported displaying the same info as Screenfetch I thought to myself, what else can we add to Neofetch?

I started adding new info functions, features, config options and Neofetch now supported displaying info like Current Terminal Emulator, Terminal Emulator Font, Device Model (Name of laptop, etc) and much more.

I'm still working on Neofetch everyday and I'm still looking for ways to extend it further. :-)

\[1\] https://github.com/dylanaraps/neofetch/issues/28


## The problem with Screenfetch

Let me start by saying this; Don't bring up the argument about bash only syntax and portability between shells. Screenfetch uses `#!/usr/bin/env bash` as it's shebang so all POSIX compliancy and portability between other shells goes out the window. Since Screenfetch is using the bash shebang, bash features **should** be used over portable ones since they're faster, more feature-full and don't spawn external processes. 

In short, the script is a mess, it's glue on top of glue.

### Quoting is inconsistent.

There's a countless amount of unquoted variables `$foo` and command substitutions `$(foo)`. Variables and command substitutions must **always** be quoted or your script will choke on whitespace and strings like this `\[*?`. 

This StackExchange answer explains it better than I can:

> Why do I need to write "$foo"? What happens without the quotes?

> $foo does not mean “take the value of the variable foo”. It means something much more complex:

>    - First, take the value of the variable.
>    - Field splitting: treat that value as a whitespace-separated list of fields, and build the resulting list. For example, if the variable contains foo *  bar ​ then the result of this step is the 3-element list foo, *, bar.
>    - Filename generation: treat each field as a glob, i.e. as a wildcard pattern, and replace it by the list of file names that match this pattern. If the pattern doesn't match any files, it is left unmodified. In our example, this results in the list containing foo, following by the list of files in the current directory, and finally bar. If the current directory is empty, the result is foo, *, bar.

> Note that the result is a list of strings. There are two contexts in shell syntax: list context and string context. Field splitting and filename generation only happen in list context, but that's most of the time. Double quotes delimit a string context: the whole double-quoted string is a single string, not to be split. (Exception: "$@" to expand to the list of positional parameters, e.g. "$@ is equivalent to "$1" "$2" "$3" if there are three positional parameters. See What is the difference between $* and $@?)

> The same happens to command substitution with $(foo) or with `foo`. On a side note, don't use `foo`: its quoting rules are weird and non-portable, and all modern shells support $(foo) which is absolutely equivalent except for having intuitive quoting rules.

> The output of arithmetic substitution also undergoes the same expansions, but that isn't normally a concern as it only contains non-expandable characters (assuming IFS doesn't contain digits or -).

> See When is double-quoting necessary? for more details about the cases when you can leave out the quotes.

> Unless you mean for all this rigmarole to happen, just remember to always use double quotes around variable and command substitutions. Do take care: leaving out the quotes can lead not just to errors but to security holes.
>
> Source: http://unix.stackexchange.com/a/131767


### Test syntax is inconsistent.

Sometimes `[` is used, other times `[[` is used.
- `[[` should be used over `[`.
    - `[[` is bash syntax whereas `[` is a builtin command.
    - `[[` is safer since variables don't have to be quoted.
    - `[[` supports more features like combining tests.


### External programs are called when bash can handle it instead.

Calling external programs should only be done when *really* necessary. Bash can handle a lot of things that Screenfetch sends to external programs. Things like string substitution and character removal can easily be done without spawning new sub processes by using variable substitutions.

Example:

```sh
# Screenfetch
cpu=$(sysctl -n hw.model | sed 's/@.*//')

# Using bash syntax.
cpu="$(sysctl -n hw.model)"
cpu="${cpu/@*}"
```

Yes, the bash method is one line larger but it removes a pipe and a call to an external program. The bash way might only be slightly faster but doing this over the course of the entire script is when you really notice a difference.


### Pipes are used too often together.

This is a continuation from the External Programs issue above. Screenfetch has command chains that pipe 4 to 5 to 6 times in one line. 

See this command taken from Screenfetch:

```sh
# 5 external programs are called and 4 pipes are used to get the CPU name from `dmesg`
cpu=$(dmesg | grep 'CPU:' | head -n 1 | sed -r 's/CPU: //' | sed -e 's/([^()]*)//g')`


# This can easily be cut down to 2 programs, 1 pipe and 2 variable substitutions.
cpu="$(dmesg | awk -F 'CPU: ' '/CPU:/ {printf $2; exit}')"`
cpu="${cpu//\(}"`
cpu="${cpu//\)}"`
```

Again, the bash way takes up more space than the Screenfetch command but it's faster and doesn't call 3 extra programs. The Screenfetch command has to wait for each program to do the following: start, process the string, exit and finally pipe the string to the next command so we can do it all again.


### There's broken code.

This should either be fixed or removed. I don't know why it's still sitting in the script when it's been known to not work for a while now.

- Screenshot uploading doesn't work at all.


### Nitpicks

These are misc issues that I think should be fixed.

- Variable naming is inconsistent.
- Function naming is inconsistent.
- Remove all `eval` usage.
    - Do you *really* need it?
- Remove all `xargs` usage.
    - Do you *really* need it?
 

## How does Neofetch differ from Screenfetch?

Although it may not seem like it, Neofetch and Screenfetch are vastly different. 

TODO