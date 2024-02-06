# WSL-targeted development with MS Visual Studio

## Introduction
This article explains the base workflow for the development with Visual Studio for the Linux projects hosted on WSL.

## Preparations
First, we must prepare the WSL Distribution image[^ksk-wsl-intro].

Then, we must install the necessary tools to our WSL image[^ms-intro].
```
sudo apt update
sudo apt install g++ gdb make ninja-build rsync zip
```

This (second) command will install the set of tools:
- A C++ compiler
- gdb
- CMake
- rsync
- zip
- An underlying build system generator


## References
[^ksk-wsl-intro]: [Windows Subsystem for Linux - the neibhour article](../WSL/Readme.md)
[^ms-intro]: [Build and debug C++ with WSL and Visual Studio - learn.microsoft.com](https://learn.microsoft.com/en-us/cpp/build/walkthrough-build-debug-wsl2?view=msvc-170)
