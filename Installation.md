This wiki page will guide you through getting neofetch working on your system.

The first and most universal way of installing neofetch is by downloading/cloning
the latest release and running the Makefile.

# Table of Contents

<!-- vim-markdown-toc GFM -->
* [Universal Install](#universal-install)
    * [Latest Release](#latest-release)
    * [Latest Git Master (Bleeding Edge)](#latest-git-master-bleeding-edge)
* [OS/Distro Packages](#osdistro-packages)
    * [Alpine Linux (edge)](#alpine-linux)
    * [Android (Termux)](#android-termux)
    * [Arch](#arch)
    * [BunsenLabs](#bunsenlabs)
    * [CRUX](#crux)
    * [Debian](#debian)
        * [Stretch / Sid (Unstable)](#stretch--sid-unstable)
        * [All other versions](#all-other-versions)
    * [Fedora / RHEL / CentOS](#fedora--rhel--centos)
    * [Gentoo / Funtoo](#gentoo--funtoo)
    * [GoboLinux](#gobolinux)
    * [iOS](#ios)
    * [macOS (Homebrew)](#macos-homebrew)
    * [NixOS](#nixos)
    * [Slackware](#slackware)
    * [Solus](#solus)
    * [Ubuntu](#ubuntu)
        * [Ubuntu 17.04 and up](#ubuntu-1704-and-up)
        * [Ubuntu 16.10 and below](#ubuntu-1610-and-below)
        * [Ubuntu daily builds](#ubuntu-daily-builds)
    * [Void Linux](#void-linux)

<!-- vim-markdown-toc -->


# Universal Install

## Latest Release

1. Download the latest release.
    - https://github.com/dylanaraps/neofetch/archive/3.2.0.tar.gz
2. Run `make install` inside the script directory to install the script.
    - **El Capitan**: `make PREFIX=/usr/local install`
    - **Haiku**: `make PREFIX=/boot/home/config/non-packaged install`
    - **NOTE**: You may have to run this as root.

## Latest Git Master (Bleeding Edge)

1. Git clone the repo.
    - `git clone https://github.com/dylanaraps/neofetch`
2. Change working directory to `neofetch`.
    - `cd neofetch`
3. Install neofetch using the Makefile.
    - `make install`
    - **El Capitan**: `make PREFIX=/usr/local install`
    - **Haiku**: `make PREFIX=/boot/home/config/non-packaged install`
    - **NOTE**: You may have to run this as root.

**NOTE:** Neofetch can be uninstalled easily using `make uninstall`. This removes
all of files from your system.

**NOTE:** You can run neofetch from any folder on your system, all the makefile
does is move the files to a "sane" location. The Makefile is optional.

# OS/Distro Packages

This section lists neofetch packages that have been made for specific OS/Distros.


## Alpine Linux (edge)

1. Neofetch is available in "testing" repository,
you need to first enable it in `/etc/apk/repositories`
2. Update repositories
    - `apk update`
3. Install the package
    - `apk add neofetch`


## Android (Termux)

Neofetch is in Termux's default repos.

1. Update repositories
    - `sudo apt-get update`
2. Install the package
    - `sudo apt-get install neofetch`


## Arch

1. Install **[neofetch](https://aur.archlinux.org/packages/neofetch/)** or **[neofetch-git](https://aur.archlinux.org/packages/neofetch-git/)** from the aur.


## BunsenLabs

Neofetch is available in the official repos.

1. Update repositories
    - `sudo apt-get update`
2. Install the package
    - `sudo apt-get install neofetch`


## CRUX

1. Install git and the git ports(8) driver
    - `sudo prt-get depinst git`
2. Add the `6c36-git` repository
    - `sudo wget -O /etc/ports/6c37-git.git "https://raw.githubusercontent.com/6c37/cross/master/git-driver/6c37-git.git"`
3. Sync the repos
    - `sudo ports -u`
4. Add the repo to /etc/prt-get.conf with your text editor of choice
    - `prtdir /usr/ports/6c37-git`
5. Install the package
    - `sudo prt-get depinst neofetch`

Or alternatively use the [port](https://raw.githubusercontent.com/6c37/crux-ports-git/3.2/neofetch/Pkgfile):

1. Download port
    - `wget -O ~/work/neofetch/Pkgfile "https://raw.githubusercontent.com/6c37/crux-ports-git/3.2/neofetch/Pkgfile"`
2. Build the package
    - `fakeroot pkgmk -d`
3. Install the package
    - `sudo pkgadd neofetch#git-*.pkg.tar.gz`


## Debian

### Stretch / Sid (Unstable)

Neofetch is in Debian Stretch/Sid's official repositories.

1. Update repositories
    - `sudo apt-get update`
2. Install the package
    - `sudo apt-get install neofetch`

NOTE: Debian `stretch` repo only contains version 2.0.2, use the third-party repo to update it to the latest version.


### All other versions

1. Add the 3rd party repo
    - `echo "deb http://dl.bintray.com/dawidd6/neofetch jessie main" | sudo tee -a /etc/apt/sources.list`
2. Add public key (you need to have curl installed)
    - `curl -L "https://bintray.com/user/downloadSubjectPublicKey?username=bintray" -o Release-neofetch.key && sudo apt-key add Release-neofetch.key && rm Release-neofetch.key`
3. Update repositories
    - `sudo apt-get update`
4. Install the package
    - `sudo apt-get install neofetch`


## Fedora / RHEL / CentOS

**NOTE**: If you are using RHEL/CentOS, change `dnf` into `yum`.

1. Make sure you have installed `dnf-plugins-core`
2. Enable COPR repository
    - `sudo dnf copr enable konimex/neofetch`
3. Install the package
    - `sudo dnf install neofetch`

Alternatively:

1. If you're using RHEL/CentOS, make sure you have installed `epel-release`
2. Fetch the repo file
  - `curl -o /etc/yum.repos.d/konimex-neofetch-epel-7.repo https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo`
    - **NOTE**: If you are using Fedora, change `epel-7` to `fedora-23`
                or your Fedora version respectively. However if you are
                using RHEL/CentOS 6, change it to `epel-6`.
3. Install the package
    - `sudo dnf install neofetch`


## Gentoo / Funtoo

You can install `app-misc/neofetch` from Gentoo/Funtoo's official repositories.

To install the git version of neofetch, use `=app-misc/neofetch-9999` instead.


## GoboLinux

Install it with the official recipe.

- `sudo Compile neofetch`


## iOS

1. Add `http://dylanaraps.com/repo` to your cydia sources.
2. Install `neofetch` through cydia.


## macOS (Homebrew)

1. Install `neofetch` with Homebrew
    - `brew install neofetch`

## NixOS

Install it from the official repositories

- `sudo nix-env -i neofetch`


## Slackware

Download the files from [SlackBuilds](https://slackbuilds.org/repository/14.2/desktop/neofetch/) and follow [their instructions](https://slackbuilds.org/howto/).


## Solus

Use the Software Center or type `sudo eopkg it neofetch`.


## Ubuntu

### Ubuntu 17.04 and up

Install it from the official repositories.

1. Update repositories
    - `sudo apt update`
2. Install the package
    - `sudo apt install neofetch`

### Ubuntu 16.10 and below

1. Add PPA
    - `sudo add-apt-repository ppa:dawidd0811/neofetch`
2. Update repositories
    - `sudo apt update`
3. Install the package
    - `sudo apt install neofetch`

### Ubuntu daily builds

This PPA contains daily builds of neofetch straight from master branch

1. Add PPA
    - `sudo add-apt-repository ppa:dawidd0811/neofetch-daily`
2. Update repositories
    - `sudo apt update`
3. Install the package
    - `sudo apt install neofetch`


## Void Linux

Install it from the official repositories

- `sudo xbps-install -S neofetch`


















