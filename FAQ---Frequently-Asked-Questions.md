### [Linux] Is Neofetch's memory output correct? 

> "\*insert program\* shows different memory amounts to Neofetch."

The correct way to calculate memory usage (and what Neofetch currently does) on Linux is the following:

```sh
MemUsed = Memtotal + Shmem - MemFree - Buffers - Cached - SReclaimable
```
Until late 2016 `htop`, `conky`, `Screenfetch`, `Neofetch` and a lot of other programs were displaying the incorrect memory usage amount. Almost all of the programs I could find have been updated to fix this but there are still a few programs displaying incorrect usage. Those of you using older versions of these programs are probably where this question comes from.

**TL;DR**: Yes

Source: [KittyKatt/screenFetch/issues/386](https://github.com/KittyKatt/screenFetch/issues/386#issuecomment-249312716)