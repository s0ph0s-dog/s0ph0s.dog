+++
title = "NixOS on the ROCKpro64"
date = "2021-10-14T03:07:50-04:00"
tags = ["sysadmin", "linux"]
audio = []
images = []
videos = []
draft = "true"
+++

Wherein a wolf learns how to get NixOS 2021.5 to boot successfully on the ROCKpro64.

<!--more-->

# Introduction

I'm trying to use a ROCKpro64 as a NAS, to help push forward the frontier of ARM for non-mobile use cases.  Because this NAS will be far away from my location most of the time, I really like NixOS's configuration system, particularly the feature where each configuration change is added as a new boot entry.  Fixing this system over the phone is much easier when all I have to do is get the person on the other end to plug in a keyboard and hit down, enter, down, enter, rather than walking them through Linux network troubleshooting by voice.

Unfortunately, installing NixOS on the ROCKpro64 was not as straightforward as I had hoped.

# Process

1. Get a working NixOS install (in a VM is fine).  It does not need to be aarch64.
2. Clone [Mic92/nixos-aarch64-images](https://github.com/Mic92/nixos-aarch64-images).
3. `cd` into the cloned directory and run `nix-build -A rockPro64`.
4. Wait patiently while the image builds.
5. `dd` the image to your SD card.
6. Obtain [an up-to-date uboot image and IDB loader for the ROCKpro64 from the NixOS build system (hydra)](https://hydra.nixos.org/job/nixpkgs/trunk/ubootRockPro64.aarch64-linux/all).
7. Find a Linux system (potentially the same NixOS one from earlier, or get a USB SD card reader and write Armbian onto a second microSD card so you can use the ROCKpro64 itself) and put the SD card into it.
7. On that Linux system, run `dd if=idbloader.img of=/dev/mmcblkX conv=fsync,notrunc bs=512 seek=64` where `/dev/mmcblkX` is the device node for the SD card.
8. Still on the Linux system, run `dd if=u-boot.itb of=/dev/mmcblkX conv=fsync,notrunc bs=512 seek=16384`, again where `/dev/mmcblkX` is your SD card's device node.
9. Put the SD card into the ROCKpro64 and attempt to boot.

# Why?

Mic92's repo as-is will not build a working image. If you try booting with the unmodified disk after imaging, it will appear to hang after
```
## Flattened Device Tree blob at 01f00000
   Booting using the fdt blob at 0x1f00000
```

This appears to be [a bug](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=973323) in the version of uboot that Mic92's tool writes into the image.

The commands above are taken from [the NixOS wiki page on the ROCKpro64](https://nixos.wiki/wiki/NixOS_on_ARM/PINE64_ROCKPro64).  The offsets seem to match the partition layout produced by Mic92's tool.

You can't write the IDB and uboot images to the SD card using `dd` on macOS. I tried, and the ROCKpro64 completely refused to boot.  This is likely some level of user error, but I didn't dive into the details enough to figure out precisely what.

# Things that are still broken

* You can't actually pick a different generation at boot with a USB keyboard.  The `extlinux_generic` bootloader doesn't have drivers for a USB keyboard.  I'm eventually going to attempt to run a Pi Zero hooked up to the serial pins as a workaround.
