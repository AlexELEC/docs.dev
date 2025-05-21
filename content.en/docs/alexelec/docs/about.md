---
title: About
weight: 10
---

## Downloading Images and System Updates

+ <a target='_blank' href="https://github.com/AlexELEC/LibreELEC-21/releases">LibreELEC</a>
+ <a target='_blank' href="https://github.com/AlexELEC/CoreELEC-21/releases">CoreELEC</a>

## Sources

+ <a target='_blank' href="https://github.com/AlexELEC/LibreELEC-21">LibreELEC</a>
+ <a target='_blank' href="https://github.com/AlexELEC/CoreELEC-21">CoreELEC</a>

## Differences from Original Versions

+ Default SSH (login/password): *root/mcpc*
+ Automatic system update feature removed from «LibreELEC/CoreELEC» settings.
+ File manager «Midnight Commander» and utility «htop» integrated into the system.
+ [«HID-Remote»](/docs/alexelec/docs/hid-remote/) service added for configuring HID remote controls.
+ Packages (dependencies) added for «TVLINK IPTV server» operation.
+ «TVLINK IPTV server» can be downloaded, activated, or deactivated in system settings.
+ «PVR TVLINK Client» integrated into the system.

**For «Kodi»:**

+ PVR-API added for «PVR TVLINK Client».
+ Channel switching speed optimized.
+ The ability to automatically change audio and video stream parameters has been added, which is necessary for «TVLINK» when it switches the stream for the same channel.
+ Repository <a target='_blank' href="https://github.com/AlexELEC/repo-21/tree/master/Omega/common">«AlexELEC Common Add-ons»</a> added,
from which you can install add-ons: «TVLINK Simple Control», «Keyboard Layout», and others.

**LibreELEC**

The ability to install packages from the <a target='_blank' href="https://wiki.coreelec.org/coreelec:entware">«Entware»</a>
repository has been added to this system (this feature is default in CoreELEC).

**CoreELEC**

The remote control configuration file (*remote.conf*) can be located in the «/storage/.config/amremote» or «/storage/.config directory».
The latter has priority.
