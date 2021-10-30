## Download

The builds can be downloaded either from [**the releases page**](https://github.com/Kron4ek/Wine-Builds/releases) or from the **[MEGA](https://mega.nz/folder/ZZUV1K7J#kIenmTQoi0if-SAcMSuAHA)** cloud. 

Some builds (stable and wayland versions) are available only on the cloud.

Due to the cloud space limitation, i delete very old builds every few years.

---

## How to use

Extract to any directory and run applications using the path to the Wine binary. For example:

    /home/username/wine-6.0-amd64/bin/wine application.exe
    
---
    
## Requirements

All regular Wine dependencies are required for these builds to work properly, including their 32-bit versions if you plan to run 32-bit applications.

The easiest way to install (almost) all required libraries is to install Wine from your distribution's package repository. I highly recommend to do this, otherwise you will have to manually figure out what libraries are needed, which may be not an easy task.

More precisely, not all the Wine dependecies are strictly required, some of them are optional and needed only for some Windows applications or only for some functions. Still, it's better to keep them all (or at least most of them) installed.

Also, do note that **glibc (libc6)** **2.27** or newer is required.

---

## Builds description

### Compilation parameters

Build flags (amd64): `-march=x86-64 -msse3 -mfpmath=sse -O2 -ftree-vectorize`

Build flags (x86): `-march=i686 -msse2 -mfpmath=sse -O2 -ftree-vectorize`

Configure options: `--without-curses --without-oss --disable-winemenubuilder --disable-win16 --disable-tests`

---

### Architectures

* **amd64** - for 64-bit systems, it can run both 32-bit and 64-bit applications.
* **x86** - for 32-bit systems, it can run only 32-bit applications.

---

### Available builds

* **Vanilla** is a Wine build compiled from the official WineHQ sources.

* **Staging** is a Wine build with [the Staging patchset](https://github.com/wine-staging/wine-staging) applied. It contains many useful patches that are not present in vanilla.

* **Staging-TkG** is a Wine build with [the Staging patchset](https://github.com/wine-staging/wine-staging) applied and with many additional useful patches. A complete list of patches is in wine-tkg-config.txt inside the build directory. Compiled from [this source code](https://github.com/Kron4ek/wine-tkg), which is generated using [the wine-tkg build system](https://github.com/Frogging-Family/wine-tkg-git).

* **Proton** is a Wine build modified by Valve and other contributors. It contains many useful patches (primarily for a better gaming experience), some of them are unique and not present in other builds. The differences from the official Steam's Proton are the lack of the Proton's python script and the lack of some builtin dlls (like DXVK and vkd3d-proton), the build environment is also different. However, you can still install DXVK and vkd3d-proton manually to your prefix, like you do with regular Wine builds.

* **Wayland** is a Wine build with the patches from the [wine-wayland project](https://github.com/varmd/wine-wayland). Wine-Wayland works only on Wayland (it doesn't work on Xorg at all) and supports only Vulkan, OpenGL is not supported. Thus you can only run Vulkan games with it (by using DXVK and vkd3d as well). Before using, read all the caveats and notes on [the wine-wayland project page](https://github.com/varmd/wine-wayland).
---

## Compilation / Build environment

I use **create_ubuntu_chroots.sh** and **build_wine.sh** to compile my Wine builds, you can use these scripts to compile your own Wine builds. The first script creates two Ubuntu chroots (32-bit and 64-bit) and the second script compiles Wine builds inside the created chroots. Optionally, you can disable the chroots usage in the **build_wine.sh** script and compile Wine builds on your host system.

These scripts are a pretty convenient way to compile your own Wine builds if you don't trust my binaries or if you want to apply different patches.

---

### Links to the sources

* https://dl.winehq.org/wine/source
* https://github.com/wine-staging/wine-staging
* https://github.com/Frogging-Family/wine-tkg-git
* https://github.com/Kron4ek/wine-tkg
* https://github.com/ValveSoftware/wine
* https://github.com/varmd/wine-wayland
* https://github.com/Kron4ek/wine-wayland
* https://gitlab.collabora.com/alf/wine/-/tree/wayland
