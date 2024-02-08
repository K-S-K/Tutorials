# WSL-targeted development with MS Visual Studio

## Introduction
This article explains the base workflow for the development with Visual Studio for the Linux projects hosted on WSL.

## Preparations
#### First, we must prepare the WSL Distribution image[^ksk-wsl-intro].
As a result of this stage, we have a clear Debian-based WSL Image, named, in my case, Debian-VSBig. Also, we have a base image archive as a restore point if we want to alter something in the flow without unnecessary time and traffic spending. The image size at this stage is 433 MB, and the backup size is 386 MB. These sizes can be other in the future; the sizes are actual for the article creation time and have only evaluation purposes.

#### Then, we must install the necessary tools to our WSL image[^ms-intro].
```
sudo apt update
```

```
sudo apt install g++ gdb make cmake ninja-build rsync zip
```

This (second) command will install the set of tools:
- A C++ compiler
- gdb
- CMake
- rsync
- zip
- An underlying build system generator

This operation will download 114 MB of data and fill 433 MB of the disk space. So, our WSL instance file on the disk will grow from 504 Mb to 1.17 Gb.

Now, when the operation is completed, let's create a backup of our image. To do that, execute the next command:
```
wsl --export Debian-VSBig D:\Polygon\Learn\WSL\Debian-VSBig-01-gpp.tar
```
The archive size at this stage is 817 Mb.


## References
[^ksk-wsl-intro]: [Windows Subsystem for Linux - the neibhour article](../WSL/Readme.md)
[^ms-intro]: [Build and debug C++ with WSL and Visual Studio - learn.microsoft.com](https://learn.microsoft.com/en-us/cpp/build/walkthrough-build-debug-wsl2?view=msvc-170)
[^medium-cmake]: [CMake Tutorial - medium.com article](https://medium.com/@onur.dundar1/cmake-tutorial-585dd180109b)
