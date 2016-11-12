- [Arch Linux](#arch)
- [Gentoo / Funtoo](#gentoo--funtoo)
- [CRUX](#crux)
- [Ubuntu](#ubuntu)
- [Debian](#debian)
- [Fedora / RHEL / CentOS](#fedora--rhel--centos)
- [Void Linux](#void-linux)
- [BunsenLabs](#bunsenlabs)
- [Solus](#solus)
- [Slackware](#slackware)
- [macOS](#mac-os-x)
- [iOS](##ios-1)
- [Android (Termux)](#android-termux)
- [Manual](#manual)


### Arch

1. Install **[neofetch](https://aur.archlinux.org/packages/neofetch/)** or **[neofetch-git](https://aur.archlinux.org/packages/neofetch-git/)** from the aur.


### Gentoo / Funtoo

You can install `app-misc/neofetch` from Gentoo/Funtoo's official repositories.

To install the git version of neofetch, use `=app-misc/neofetch-9999` instead.


### CRUX

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


### Ubuntu

1. Add PPA
    - `sudo add-apt-repository ppa:dawidd0811/neofetch`
2. Update repositories
    - `sudo apt update`
3. Install the package
    - `sudo apt install neofetch`


### Debian

1. Add the 3rd party repo
    - `echo "deb http://dl.bintray.com/dawidd6/neofetch jessie main" | sudo tee -a /etc/apt/sources.list`
2. Add public key (you need to have curl installed)
    - `curl -L "https://bintray.com/user/downloadSubjectPublicKey?username=bintray" -o Release-neofetch.key && sudo apt-key add Release-neofetch.key && rm Release-neofetch.key`
3. Update repositories
    - `sudo apt-get update`
4. Install the package
    - `sudo apt-get install neofetch`


### Fedora / RHEL / CentOS

**NOTE**: If you are using RHEL/CentOS, change `dnf` into `yum`.

1. Make sure you have installed `dnf-plugins-core`
2. Enable COPR repository
    - `sudo dnf copr enable konimex/neofetch`
3. Install the package
    - `sudo dnf install neofetch`

Alternatively:

1. Change your working directory to `/etc/yum.repos.d/`
2. Fetch the repo file
    - `wget https://copr.fedorainfracloud.org/coprs/konimex/neofetch/repo/epel-7/konimex-neofetch-epel-7.repo`
        * **NOTE**: If you are using Fedora, change `epel-7` to `fedora-23` or your Fedora version respectively. However if you are using RHEL/CentOS 6, change it to `epel-6`.
3. Install the package
    - `sudo dnf install neofetch`


### Void Linux

Install it from the official repositories

- `sudo xbps-install -S neofetch`


### BunsenLabs

Neofetch is available in the official repos.

1. `sudo apt-get update`
2. `sudo apt-get install neofetch`


### Solus

Use the Software Center or type `sudo eopkg it neofetch`.


### Slackware

Download the files from [SlackBuilds](https://slackbuilds.org/repository/14.2/desktop/neofetch/) and follow [their instructions](https://slackbuilds.org/howto/).


### macOS

1. Install `neofetch` with Homebrew
    - `brew install neofetch`


### iOS

1. Add `http://dylanaraps.com/repo` to your cydia sources.
2. Install `neofetch` through cydia.


### Android (Termux)

You can install it using `apt install neofetch`


### Manual

1. Download the latest source at https://github.com/dylanaraps/neofetch
2. Run `make install` inside the script directory to install the script.
    - **El Capitan**: `PREFIX=/usr/local make install`

**NOTE:** Neofetch can be uninstalled easily using `make uninstall`.

**NOTE:** You can run neofetch from any folder on your system, all the makefile does is move the files to a
"sane" location. The makefile is optional.

