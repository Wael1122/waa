**NOTE:** This page is a WIP

The goal of this wiki page is to answer these questions:

- How is Neofetch different from Screenfetch?
- What's wrong with Screenfetch?


## Table of Contents

<!-- vim-markdown-toc GFM -->
* [Why was Neofetch created?](#why-was-neofetch-created)
* [The problem with Screenfetch](#the-problem-with-screenfetch)
    * [Everything is hard-coded.](#everything-is-hard-coded)
    * [Quoting is inconsistent.](#quoting-is-inconsistent)
    * [Test syntax is inconsistent.](#test-syntax-is-inconsistent)
    * [External programs are called when bash can handle it instead.](#external-programs-are-called-when-bash-can-handle-it-instead)
    * [Pipes are used too often together.](#pipes-are-used-too-often-together)
    * [Useless `cat` usage.](#useless-cat-usage)
    * [Pointless use of `echo`.](#pointless-use-of-echo)
    * [Broken code.](#broken-code)
    * [Small problems.](#small-problems)
* [How does Neofetch differ from Screenfetch?](#how-does-neofetch-differ-from-screenfetch)
    * [Operating Systems](#operating-systems)
    * [Info](#info)
    * [Speed](#speed)
    * [Syntax](#syntax)
    * [Ascii Art](#ascii-art)
    * [Images](#images)
    * [Customization](#customization)

<!-- vim-markdown-toc -->


## Why was Neofetch created?

Neofetch or as it was originally called `fetch` was never meant to be a replacement for Screenfetch nor was it ever meant to display Ascii logos. Neofetch first started as my `70` line hard-coded script that only supported Arch Linux, only displayed a tiny amount of info and only supported showing images with w3m-img.

I started posting screenshots of my system to [/r/unixporn/](https://reddit.com/r/unixporn) which included my tiny little script. People started using the script and started asking me to add support for their Linux Distros and later their Operating systems. Happy to see that others were using something that I created, I started adding support various Distros and Operating systems.

![Oldest screenshot of fetch](https://u.teknik.io/h7KSz.png)
<br \><sub>Oldest screenshot of `fetch`</sub>

When it came to adding support for Mac OS I realized that I had hit a stopping point. The script wasn't written in a way that would allow me to easily expand it to more Operating systems; it needed a rewrite. So I (re)wrote the script from scratch over an entire weekend and the result is the script base/structure that Neofetch is still using today.

I continued to work on Neofetch every day and whenever someone suggested a feature, I would add it no questions asked. One day a user by the name of [@aloisdg](https://github.com/dylanaraps/neofetch/issues/28) opened a bug report on the repo requesting "ascii art support". \[1\] I jumped on this and was shocked to see how easy it was to implement, I had a working version the same day and it was in master a day later.

![early distro ascii support](https://camo.githubusercontent.com/92b2d32b4f1d22b6fb2dbb680417c8a91a5b8f3b/687474703a2f2f692e696d6775722e636f6d2f744746664b4b302e706e67)
<br \><sub>Early distro ascii support</sub>

As I continued working on Neofetch every day, looking for ways to improve it I decided to get it to feature parity with Screenfetch. Once Neofetch supported displaying the same info as Screenfetch I thought to myself; what else can we add to Neofetch?

I started adding new info functions, features, config options and Neofetch eventually supported displaying info like Current Terminal Emulator, Terminal Emulator Font, Device Model (Name of laptop, etc.) and much more.

I continue to work on Neofetch every day and I'm still looking for ways to extend it further. :-)

\[1\] https://github.com/dylanaraps/neofetch/issues/28


## The problem with Screenfetch

I'll be blunt. The script is a mess, it's glue on top of glue.

Let me start by saying this: Don't bring up the argument about bash only syntax and portability between shells. Screenfetch uses `#!/usr/bin/env bash` as its shebang so all POSIX compliancy and portability between other shells goes out the window. Since Screenfetch is using the bash shebang, bash features **should** be used over portable ones since they're faster, more feature-full and don't spawn external processes.

Screenfetch constantly mixes POSIX syntax with BASH only syntax for no apparent reason. The whole script is an inconsistent mess; variables/functions are all named differently; `printf`/`echo` are mixed and matched throughout and there's even useless `cat` usage!

Screenfetch is slow. Due to the issues with quoting, external programs and pipes, Screenfetch chokes. Its littered with unquoted variables/command substitution, endless piping and external program use when bash can do it built-in.

Screenfetch needs maintainers who aren't scared of refactoring large parts of the script. All of these issues can be fixed if someone is willing to put the work in. As it stands right now, Screenfetch is unmaintainable. Good luck making any changes larger than distro additions or small bug fixes.


### Everything is hard-coded.

Screenfetch hard-codes almost everything. Inside the script you'll find long hard-coded lists of Window Manager and Desktop Environment process names, hard-coded Distro Names, hard-coded file names and more. This is really bad and should be avoided altogether if possible.

There are times when hard-coding things is necessary but this should only be done when you've exhausted all other options and it's a last resort. Neofetch has a few cases of hard-coded strings like in the CPU/GPU detection on iOS devices. This was necessary since there's no dynamic way of getting this information and It was a last resort, after hours of testing.

The hard-coded parts of Screenfetch could've all been easily avoided, this is true because Neofetch doesn't suffer from the same problems.


**hard-coded Window Manager and Desktop Environment lists.**

Screenfetch loops over these lists, checking the running processes on the system until it finds the Window Manager or Desktop Environment that is running. This is very inefficient and requires manual intervention if the Window Manager or Desktop Environment isn't in the lists above.

```sh
wmnames=( fluxbox openbox blackbox xfwm4 metacity kwin twin icewm pekwm flwm flwm_topside fvwm dwm awesome wmaker stumpwm musca xmonad.* i3 ratpoison scrotwm spectrwm wmfs wmii beryl subtle e16 enlightenment sawfish emerald monsterwm dminiwm compiz Finder herbstluftwm howm notion bspwm cinnamon 2bwm echinus swm budgie-wm dtwm 9wm chromeos-wm deepin-wm sway )
denames=( gnome-session xfce-mcs-manage xfce4-session xfconfd ksmserver lxsession lxqt-session gnome-settings-daemon mate-session mate-settings-daemon Finder deepin )
```


**Distro release files are hard-coded.**

Take a look at this chunk of code taken from Screenfetch, distro release file names are all hard-coded. This is only a small chunk of the distro detection, the entire block is humongous. This type of detection is bad because this block will have to be added to every-time a new distro is added to Screenfetch.

```sh
elif [ -f /etc/frugalware-release ]; then distro="Frugalware"
elif [ -f /etc/fux-release ]; then distro="Fux"
elif [ -f /etc/gentoo-release ]; then
    if grep -q "Funtoo" /etc/gentoo-release ; then
        distro="Funtoo"
    else
        distro="Gentoo"
    fi
elif [ -f /etc/kogaion-release ]; then distro="Kogaion"
elif [ -f /etc/mageia-release ]; then distro="Mageia"
elif [ -f /etc/mandrake-release ]; then
```


**Distro names are hard-coded.**

Due to the detection methods Screenfetch uses, the distro names are detected all in lowercase or as short versions. Screenfetch then has a giant case statement with the sole purpose of fixing capitalization and naming of Distros. If Screenfetch used proper detection methods then this entire block wouldn't be needed at all.

Note: This is a tiny chunk of the case statement. The entire thing is too long to add here.

```sh
case $distro in
		alpine) distro="Alpine Linux" ;;
		antergos) distro="Antergos" ;;
		arch*linux*old) distro="Arch Linux - Old" ;;
		arch|arch*linux) distro="Arch Linux" ;;
		blag) distro="BLAG" ;;
		bunsenlabs) distro="BunsenLabs" ;;
		centos) distro="CentOS" ;;
		chakra) distro="Chakra" ;;
		chapeau) distro="Chapeau" ;;
		chrome*|chromium*) distro="Chrome OS" ;;
		crunchbang) distro="CrunchBang" ;;
		crux) distro="CRUX" ;;
		cygwin) distro="Cygwin" ;;
		debian) distro="Debian" ;;
		devuan) distro="Devuan" ;;
		deepin) distro="Deepin" ;;
		dragonflybsd) distro="DragonFlyBSD" ;;
		dragora) distro="Dragora" ;;
# ...
```

**Window manager names are hard-coded.**

Same reasons as above. Here's a chunk from Screenfetch:

```sh
case ${WM} in
    *'gala'*) WM="Gala";;
    '2bwm') WM="2bwm";;
    'awesome') WM="Awesome";;
    'beryl') WM="Beryl";;
    'blackbox') WM="BlackBox";;
    'budgiewm') WM="BudgieWM";;
    'chromeos-wm') WM="chromeos-wm";;
    'cinnamon') WM="Cinnamon";;
    'compiz') WM="Compiz";;
    'deepin-wm') WM="Deepin WM";;
    'dminiwm') WM="dminiwm";;
    'dwm') WM="dwm";;
# ...
```

**Package manager detection is hard-coded..**

Screenfetch hard-codes package managers to specific OS/Distros. This is again bad because it requires manual intervention when adding new OS/Distros. Neofetch on the other hand detects which package managers are installed and uses those instead.

This is a small chunk taken from Screenfetch which shows the hard-coded Package Manager detection.

```sh
case "${distro}" in
		'Alpine Linux') pkgs=$(apk info | wc -l) ;;
		'Arch Linux'|'Parabola GNU/Linux-libre'|'Chakra'|'Manjaro'|'Antergos'|'Netrunner'|'KaOS'|'Obarun') pkgs=$(pacman -Qq | wc -l) ;;
		'Dragora') pkgs=$(ls -1 /var/db/pkg | wc -l) ;;
		'Frugalware') pkgs=$(pacman-g2 -Q | wc -l) ;;
		'Fuduntu'|'Ubuntu'|'Mint'|'KDE neon'|'Debian'|'Devuan'|'Raspbian'|'LMDE'|'CrunchBang'|'Peppermint'|'LinuxDeepin'|'Deepin'|'Kali Linux'|'Trisquel'|'elementary OS'|'gNewSense'|'BunsenLabs'|'SteamOS') pkgs=$(dpkg -l | grep -c ^i) ;;
		'Slackware') pkgs=$(ls -1 /var/log/packages | wc -l) ;;
		'Gentoo'|'Sabayon'|'Funtoo'|'Chrome OS'|'Kogaion') pkgs=$(ls -d /var/db/pkg/*/* | wc -l) ;;
		'NixOS') pkgs=$(ls -d -1 /nix/store/*/ | wc -l) ;;
		'Fedora'|'Fux'|'Korora'|'BLAG'|'Chapeau'|'openSUSE'|'SUSE Linux Enterprise'|'Red Hat Enterprise Linux'|'ROSA'|'Oracle Linux'|'CentOS'|'Mandriva'|'Mandrake'|'Mageia'|'Mer'|'SailfishOS'|'PCLinuxOS'|'Viperr'|'Qubes OS'|'Red Star OS') pkgs=$(rpm -qa | wc -l) ;;
		'Void') pkgs=$(xbps-query -l | wc -l) ;;
		'Evolve OS'|'Solus') pkgs=$(pisi list-installed | wc -l) ;;
		'CRUX') pkgs=$(pkginfo -i | wc -l) ;;
		'Lunar Linux') pkgs=$(lvu installed | wc -l) ;;
		'TinyCore') pkgs=$(tce-status -i | wc -l) ;;
```


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

### Useless `cat` usage.

Screenfetch calls the external program `cat` when it's totally unnecessary. As of me writing this wiki page there are 10~ unnecessary uses of `cat` in Screenfetch. They can all easily be avoided by replacing the word `cat` with `< `. `<` is a bash builtin and doesn't spawn external programs.

```sh
# Screenfetch
[[ "$(cat /etc/os-release)" =~ "Raspbian" ]]

# Bash - No external processes.
[[ "$(< /etc/os-release)" =~ "Raspbian" ]]

# Screenfetch
distro_more="$(cat /usr/share/doc/tc/release.txt)"

# Bash - No external processes.
distro_more="$(< /usr/share/doc/tc/release.txt)"
```

### Pointless use of `echo`.

`echo -e` is used when assigning variables for some odd reason.

```sh
# Screenfetch
mydistro=$(echo -e "$labelcolor OS:$textcolor $distro $sysArch")

# Correct way
mydistro="$labelcolor OS:$textcolor $ditro $sysArch"

# Screenfetch
for l in $(echo $distrib_id); do

# Correct way
for l in "$distrib_id"; do

# Screenfetch
if [ $(echo $cpu_mhz) -gt 999 ]; then

# Correct way
if ((cpu_mhz > 999)); then
```

### Broken code.

This should either be fixed or removed. I don't know why it's still sitting in the script when it's been known to not work for a while now.

- Screenshot uploading doesn't work at all.


### Small problems.

These are misc issues that I think should be fixed.

- Variable naming is inconsistent.
- Function naming is inconsistent.
- Remove all `eval` usage.
    - Do you *really* need it?
- Remove all `xargs` usage.
    - Do you *really* need it?
- Remove all `bc` usage.
    - Do you *really* need it?
- There's inconsistent use of `printf` / `echo`.
    - Pick one, use it. Don't mix and match.
- There's  still traces of backticks used through the script.
    - You're using bash, there's no reason not to use. `$()`


## How does Neofetch differ from Screenfetch?

Neofetch and Screenfetch may look alike but they're vastly different underneath. For starters, Neofetch is a far newer codebase and was designed to support multiple Operating Systems from the start. This allows Neofetch to expand to new Operating Systems and Distros effortlessly.

Neofetch is in (and has always been in) very active development, with myself and a few others continuously working on improving Neofetch everyday for the foreseeable future.

Neofetch is clean; the script has a clear structure and you can learn how it works very easily.

There's nothing Screenfetch does that Neofetch doesn't do better. Neofetch is faster, more customizable, supports more operating systems, displays more info and isn't a fucking mess on the inside.


### Operating Systems

Neofetch supports more operating systems than the other tools out there. Neofetch currently supports Linux, MacOS, iOS, BSD, Solaris, Android, Haiku, GNU Hurd and Windows (Cygwin/Windows 10 Linux subsystem). Neofetch can run on anything bash runs on, if your OS isn't supported then open an issue here on github and I'll get right to it.

See this wiki page for full OS support: [OS Support](https://github.com/dylanaraps/neofetch/wiki/Operating-System-Support)


### Info

Neofetch supports displaying all of the info Screenfetch displays plus a lot more. Every function in Neofetch also includes options for customization though the config file and command-line launch flags. 

For example: The `CPU` function has 5 different options with multiple values that let you customize every aspect of the output. CPU speed can be changed to `current`, `min`, `max`, `bios` or even turned off completely. You can hide the CPU `brand`, `name` or both. You can show `logical`, `physical` or no CPU cores. And you can even show or hide CPU temperature.

See the config file for documentation on all of the options:

https://github.com/dylanaraps/neofetch/wiki/Config-File


These are the Neofetch exclusive functions:

- **Battery**: Print the battery level of your device.
- **Birthday**: Print the date the OS was installed.
- **CPU Usage**: Print CPU Usage.
- **Local IP**: Print the local IP address.
- **Model**: Print the device model of your device.
- **Public IP**: Print the public IP address.
- **Terminal Emulator**: Print the terminal emulator Neofetch is running in.
- **Terminal Emulator Font**: Print the terminal emulator font.
- **Song**: Print the currently playing song.
- **Users**: Print the currently logged in users.

Neofetch also supports displaying your terminal colors as blocks.

![blocks](https://u.teknik.io/kcpQl.png)


### Speed

Neofetch is stupid fast.

Neofetch only spawns external processes when it makes sense and uses built in bash features wherever possible. All variables and command substitutions are correctly quoted so we don't choke on whitespace.

Compare the latest master of Neofetch to the latest master of Screenfetch and you'll find that Neofetch (in ascii mode) is 3 times faster than Screenfetch on average. This is all while Neofetch is displaying more system information and your terminal colors.

Despite Image mode being much slower, Neofetch is still on average 70ms faster than Screenfetch.

```sh
# Testing details
# Lenovo YOGA 900
# Arch Linux
# Neofetch    - 2bd0379d9042b43d621f618e759e22e609521b57
# Screenfetch - 5f15e57932292b0a750cf0a95c714f04018eeaa0

# Neofetch - Ascii mode
# Result: real 0m0.101s
#         user 0m0.037s
#         sys  0m0.010s
time neofetch --config off --ascii

# Neofetch - Image mode
# Result: real 0m0.251s
#         user 0m0.063s
#         sys  0m0.047s
time neofetch --config off

# Screenfetch
# Result: real 0m0.341s
#         user 0m0.133s
#         sys  0m0.053s
time screenfetch

```

### Syntax

Neofetch takes full advantage of Bash 3 syntax/features. We don't mix and match POSIX syntax with Bash syntax, we keep it consistent throughout.

All functions and variables follow the same naming scheme `example_of_scheme`. This makes it a lot easier to find things when working on the script.


### Ascii Art

Neofetch stores the ascii art as separate plain text files that are then read only when needed. The script isn't littered with a huge case statement with hard-coded info variables.

The only downside to this implementation is that Neofetch and the ascii logos can't be distributed as a single file. This is fine since the Makefile can easily install/uninstall Neofetch without issue.


### Images

Neofetch supports displaying full color images in place of the ascii art by using `w3m-img`, `tycat` or `iTerm2`.

See this wiki page for more info: [Images in the terminal](https://github.com/dylanaraps/neofetch/wiki/Images-in-the-terminal)


### Customization

Neofetch is highly customizable. Neofetch has a config file that includes the `print_info()` function which gives you total freedom over how the info is displayed. The config file also includes over 50 options for customizing the various aspects of Neofetch.

Every config option also has a corresponding launch flag. For example, the config option `$speed_type` has a launch flag called `--speed_type`.

- See this link for the config file: [Config file](https://github.com/dylanaraps/neofetch/blob/master/config/config)
- See this wiki page for more info: [Customizing info](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info)

