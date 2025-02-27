<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/RcloneBrowserLongLogo1.png" width=80%>

[![Travis CI Build Status][img1]][1] [![AppVeyor Build Status][img2]][2] [![Downloads][img3]][3] [![Release][img4]][4] [![License][img5]][5] <img src="https://img.shields.io/badge/Qt-cmake-green.svg"> [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/kapitainsky)




Rclone browser
==============
Simple cross platfrom GUI for [rclone](https://rclone.org/) command line tool.

Supports macOS, GNU/Linux and Windows.

Table of contents
-------------------
* [Features](https://github.com/kapitainsky/RcloneBrowser#features)
* [Sample screenshots](https://github.com/kapitainsky/RcloneBrowser#sample-screenshots)
* [How to get it](https://github.com/kapitainsky/RcloneBrowser#how-to-get-it)
* [Build instructions for Linux](https://github.com/kapitainsky/RcloneBrowser#build-instructions-for-linux)
* [Build instructions for FreeBSD](https://github.com/kapitainsky/RcloneBrowser#build-instructions-for-freebsd)
* [Build instructions for macOS](https://github.com/kapitainsky/RcloneBrowser#build-instructions-for-macos)
* [Build instructions for Windows](https://github.com/kapitainsky/RcloneBrowser#build-instructions-for-windows)
* [History](https://github.com/kapitainsky/RcloneBrowser#history)
* [Code signing certificates donations](https://github.com/kapitainsky/RcloneBrowser#code-signing-certificates-donations)
* [License](https://github.com/kapitainsky/RcloneBrowser#license)


Features
--------

* Allows to browse and modify any rclone remote, including encrypted ones
* Uses same configuration file as rclone, no extra configuration required
* Supports custom location and encryption for `.rclone.conf` configuration file
* Simultaneously navigate multiple repositories in separate tabs
* Lists files hierarchically with file name, size and modify date
* All rclone commands are executed asynchronously, no freezing GUI
* File hierarchy is lazily cached in memory, for faster traversal of folders
* Allows to upload, download, create new folders, rename or delete files and folders
* Allows to calculate size of folder, export list of files and copy rclone command to clipboard
* Can process multiple upload or download jobs in background
* Drag & drop support for dragging files from local file explorer for uploading
* Streaming media files for playback in player like [vlc][6] or similar
* Mount and unmount folders on macOS, GNU/Linux and Windows (for Windows requires [winfsp](http://www.secfs.net/winfsp/))
* Optionally minimizes to tray, with notifications when upload/download finishes
* Supports portable mode (create .ini file next to executable with same name), rclone and .rclone.conf path now can be relative to executable
* Supports drive-shared-with-me (Google Drive specific)
* For remotes supporting public link sharing has an option (right-click menu) to fetch it
* Supports tasks. Created jobs can be saved and run or edited later. 

Sample screenshots
-------------------
### macOS
<p align="center">
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot24.png" width=100%>
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot23.png" width=75%>
</p>


### Linux
<p align="center">
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot21.png" width=65%>
</p>
</br>
<p align="center">
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot22.png" width=65%>
</p>
</br>


### Windows
<p align="center">
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot25.PNG" width=100%>
</p>
</br>
<p align="center">
<img src="https://github.com/kapitainsky/RcloneBrowser/wiki/images/screenshot26.PNG" width=65%>
</p>
</br>



How to get it
--------------
Get Windows, macOS, Ubuntu/Debian (including Raspberry Pi version) and universal AppImage for all other 64bit Linux versions - on [releases][3]' page.

All released binaries are signed with my [PGP key](https://github.com/kapitainsky/RcloneBrowser/wiki/PGP-key). It allows to verify that provided binaries were created by myself and are unchanged. If you would like to have properly signed releases with code signing certificates please see note at the end of this section.

ArchLinux users can install latest release from AUR repository: [rclone-browser][7]. It has been updated to this repo.

Starting with the next release I will provide proper installers for Windows releases and for Linux AppImage only. Some explanation on latter... Binaries for Linux desktop applications is a major f*ing pain in the ass... as Linus Torvalds said - [DebConf 14_ QA](https://www.youtube.com/watch?v=5PmHRSeA2c8) at 05:40:

> I'm talking about actual application writers that want to make a package of their application for Linux. And I've seen this firsthand with the other project I've been involved with, which is my divelog application.
> We make binaries for Windows and OS X. 

He is talking about [Subsurface](https://subsurface-divelog.org). His small side project.

> We basically don't make binaries for Linux. Why? Because binaries for Linux desktop applications is a major f*ing pain in the ass. Right. You don't make binaries for Linux. You make binaries for Fedora 19, Fedora 20, maybe there's even like RHEL 5 from ten years ago, you make binaries for debian stable.
> Or actually you don't make binaries for debian stable because debian stable has libraries that are so old that anything that was built in the last century doesn't work. But you might make binaries for debian... whatever the codename is for unstable. And even that is a major pain because (...) debian has those rules that you are supposed to use shared libraries. Right.

> And if you don't use shared libraries, getting your package in, like, is just painful. 
> But using shared libraries is not an option when the libraries are experimental and the libraries are used by two people and one of them is crazy, so every other day some ABI breaks. 
> So you actually want to just compile one binary and have it work. Preferably forever. And preferably across all Linux distributions. 
> And I actually think distributions have done a horribly, horribly bad job.

> One of the things that I do on the kernel - and I have to fight this every single release and I think it's sad - we have one rule in the kernel, one rule: we don't break userspace. (...) People break userspace, I get really, really angry. (...) 
> And then all the distributions come in and they screw it all up. Because they break binary compatibility left and right. 
> They update glibc and everything breaks. (...) 
> So that's my rant. And that's what I really fundamentally think needs to change for Linux to work on the desktop because you can't have applications writers to do fifteen billion different versions.

And I totally agree with above. I want to provide binary which works across as many Linux distributions as possible and I dont have time to fight with all mess with different dependencies etc. There are other similar ditribution formats e.g. flatpak but I had to choose one and I decided that AppImage is my best choice. I am not saying that AppImage is the best one but it nicely fits my objectives. You can see comparison of different solutions [here](https://github.com/AppImage/AppImageKit/wiki/Similar-projects#comparison).

If for whatever reason you are not happy or your system is not covered with provided binaries you can easily build Rclone Browser for yourself. Especially on Unix-like systems it is very easy. Please see below step by step instructions for major operating systems. I have tested all of them and you can have your own Linux distribution Rclone Browser running in few minutes.

Note: For Windows and macOS it would be much nicer (to avoid pop ups about unknown software origin) to properly sign released packages with code signing certificates however it does not come free even for open source software. I looked at it and it seems that to get keys for both systems for the next three years would cost about $500 (3x$99 for [Apple developer account](https://developer.apple.com/support/purchase-activation/) and $200 for cheapest Comodo [code signing certificate](https://comodosslstore.com/uk/code-signing). I am not prepared to budget it as I do this only as a hobby and I am enirely happy with this software as it is. If Rclone Browser users think that properly signed software would be beneficial for them they can [chip in](https://www.paypal.me/kapitainsky) some cash for it. If I raise required amount I will get keys. If not I will give money to some charity.



Build instructions for Linux
------------------------------------------
1. Install dependencies:
* Debian/Ubuntu and derivatives: `sudo apt update && sudo apt -y install git g++ cmake make qtdeclarative5-dev` 
* Suse/OpenSuse: `sudo zypper ref && sudo zypper --non-interactive install git cmake make gcc-c++ libQt5Core-devel libQt5Widgets-devel libQt5Network-devel`
* RHEL/CentOS: `sudo yum -y install git gcc-c++ cmake make qt5-qtdeclarative`
* Fedora: `sudo dnf -y install git g++ cmake make qt5-qtdeclarative-devel`
* Arch/Manjaro: `sudo pacman -Sy --noconfirm --needed git gcc cmake make qt5-declarative`
2. Clone source code from this repo `git clone https://github.com/kapitainsky/RcloneBrowser.git`
3. Go to source folder `cd RcloneBrowser`
4. Create new build folder - `mkdir build && cd build`
5. Run `cmake ..` from build folder to create makefile
6. Run `make` from build folder to create binary
7. Install `sudo make install`


Build instructions for FreeBSD
------------------------------
1. Install dependencies `sudo pkg install git cmake qt5-buildtools qt5-declarative qt5-qmake`
2. Clone source code from this repo `git clone https://github.com/kapitainsky/RcloneBrowser.git`
3. Go to source folder `cd RcloneBrowser`
4. Create new build folder - `mkdir build && cd build`
5. Run `cmake ..` from build folder to create makefile
6. Run `make` from build folder to create binary
7. Install `sudo make install`

Note: For rclone remotes mount to work please see this forum [thread](https://forum.rclone.org/t/failed-to-mount-fuse-fs-freebsd/7723/9). For me it was enough to run `sudo sysctl vfs.usermount=1`


Build instructions for macOS
----------------------------
1. If you don't have Homebrew yet install it `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
2. Install dependencies `brew install git cmake rclone qt5`
3. Set Qt environment variables `export PATH="/usr/local/opt/qt/bin:$PATH" &&  export LDFLAGS="-L/usr/local/opt/qt/lib" &&  export CPPFLAGS="-I/usr/local/opt/qt/include" && export PKG_CONFIG_PATH="/usr/local/opt/qt/lib/pkgconfig"`. You can add this to your .bashrc (assuming you use bash) if you want to keep it persistent
4. Clone source code from this repo `git clone https://github.com/kapitainsky/RcloneBrowser.git`
5. Go to source folder `cd RcloneBrowser`
6. Create new build folder - `mkdir build && cd build`
7. Run `cmake ..` from build folder to create makefile
8. Run `cmake --build .` from build folder to create binary
9. Go to yet another newly created build folder `cd build`. Your binary should be here
10. Package your binary with Qt libraries to create self-contained application `macdeployqt rclone-browser.app -executable="rclone-browser.app/Contents/MacOS/rclone-browser" -qmldir=../src/`. Without this step binary won't work without Qt installed


Build instructions for Windows
------------------------------
1. Get [Visual Studio 2019][8] - you need "Desktop development with C++" module only
2. Install [CMake][9]
3. Install latest Qt v5 (64-bit) from [Qt website][10]. You only need "Qt 5.13.2 Prebuilt Components for MSVC 2017 64-bit" (MSVC 2017 64-bit). Later steps assume you install it in c:\Qt
4. Get rclone-browser source code. You either need to install git and clone it or download zip file from [releases][3]
5. Go to source folder `cd RcloneBrowser`
6. From cmd create new build folder  - `mkdir build` and then `cd build`
7. run `cmake -G "Visual Studio 16 2019" -A x64 -DCMAKE_CONFIGURATION_TYPES="Release" -DCMAKE_PREFIX_PATH=c:\Qt\5.13.2\msvc2017_64 .. && cmake --build . --config Release`
8. run `c:\Qt\5.13.2\msvc2017_64\bin\windeployqt.exe --no-translations --no-angle --no-compiler-runtime --no-svg ".\build\Release\RcloneBrowser.exe"`
9. build\Release folder contains now RcloneBrowser.exe binary and all other files required to run it
10. If your system does not have required MSVC runtime you can install one from Microsoft [website](https://support.microsoft.com/en-gb/help/2977003/the-latest-supported-visual-c-downloads).


History
--------
Being rclone-browser user for some time and got annoyed by small not working bits and pieces I decided for DYI approach and this is how this repo was created. Original repo (https://github.com/mmozeiko/RcloneBrowser) has not been touched for years and in the meantime rclone changed few things breaking some rclone-browser functionality.

I've looked around but could not find anything fully working. Some github users made progress in fixing and adding stuff so I've built upon it.

I used DinCahill's changes (https://github.com/DinCahill/RcloneBrowser) as a base of my version.

I have fixed whatever I found still not working and added few minor tweaks. I've recompiled and repackaged everything using latest Qt (5.13.1). This on its own fixed some issues and added new features like support for dark mode in macOS.

Code signing certificates donations 
---------------------------

If you would like to donate towards code signing keys please feel free to do it. If I don't raise required $500 I will give all money to some charity. Please see my note regarding it at the end of [How to get it](https://github.com/kapitainsky/RcloneBrowser#how-to-get-it) section. I will keep all updated with amount raised.

https://www.paypal.me/kapitainsky

License
-------
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

[1]: https://travis-ci.org/kapitainsky/RcloneBrowser
[2]: https://ci.appveyor.com/project/kapitainsky/RcloneBrowser
[3]: https://github.com/kapitainsky/RcloneBrowser/releases
[4]: https://github.com/kapitainsky/RcloneBrowser/releases/latest
[5]: https://github.com/kapitainsky/RcloneBrowser/blob/master/LICENSE
[6]: https://www.videolan.org
[7]: https://aur.archlinux.org/packages/rclone-browser
[8]: https://docs.microsoft.com/en-us/visualstudio/releases/2019/release-notes
[9]: http://www.cmake.org/
[10]: https://www.qt.io/download-open-source/
[img1]: https://api.travis-ci.org/kapitainsky/RcloneBrowser.svg?branch=master
[img2]: https://ci.appveyor.com/api/projects/status/cclx7jc48t4u4x9u?svg=true
[img3]: https://img.shields.io/github/downloads/kapitainsky/RcloneBrowser/total.svg?maxAge=3600
[img4]: https://img.shields.io/github/release/kapitainsky/RcloneBrowser.svg?maxAge=3600
[img5]: https://img.shields.io/github/license/kapitainsky/RcloneBrowser.svg?maxAge=2592000


