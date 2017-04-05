## WIP

### [Linux] Is Neofetch's memory output correct? 

> "\*insert program\* shows different memory amounts to Neofetch."

The correct way to calculate memory usage (and what Neofetch currently does) on Linux is the following:

```sh
MemUsed = Memtotal + Shmem - MemFree - Buffers - Cached - SReclaimable
```
Until late 2016 `htop`, `conky`, `Screenfetch`, `Neofetch` and a lot of other programs were displaying the incorrect memory usage amount. Almost all of the programs I could find have been updated to fix this but there are still a few programs displaying incorrect usage. Those of you using older versions of these programs are probably where this question comes from.

Source: [KittyKatt/screenFetch/issues/386](https://github.com/KittyKatt/screenFetch/issues/386#issuecomment-249312716)

**TL;DR**: Yes


### [Linux] Neofetch reports inaccurate distro name

>It's supposed to be [insert a downstream distro here], but it shows [insert an upstream distro here] instead!

The prominent case is with Antergos and Arch, with `lsb-release` installed. When Neofetch detects a Linux distro, they look for `lsb-release` command before searching for the `/etc/os-release` file. Because some downstream distros mostly utilizes their upstream distro's repository, that means unless they supply their own `lsb-release` package in their own repository, that means they will use upstream's `lsb-release`, and as a result, the `Distro` output will be the upstream one. We had deleted support for lsb_release, but more complaints come right after we deleted it because it proved to be useful in detecting distros (as *most* distros filled them in properly, see [issues/493](https://github.com/dylanaraps/neofetch/issues/493)), so we had to reinstate it.

>So, shouldn't you add an exception rule in cases like these?

A good distro will always provide their own `lsb-release` file, otherwise they will be practically seen as the upstream distro with fancy modifications.

>So, is there any workaround?

Yes, actually. You'd have to remove your `lsb-release` (or any equivalent) package. (That is, if the distro filled their `/etc/*-release` properly. Contact your distro's maintainers if they don't).