# Windows Subsystem for Linux

## Abstract
Sometimes, we need to create some elementary things to provide a proper environment for a project. As we don't perform these things every day we can forget some details and we'll be forsed to spend nights to google it. It is reaaly better to have the short form of the information in the understandable form.

## Introduction
The article covers several tiny activities:
- Basic WSL commands;
- Creating the WSL distribution of the desired type;
- Accessing the working WSL distribution command line;
- Creating the restore points of the WSL distribution instance;
- Creating the clones of the distribution for different experiments.

## Some of the Basic WSL Commands
The commands I use in the job, described in the article, are:
- ```wsl --list --all -v``` - Get the list of WSL Distributions we have registered on the local machine
- ```wsl --list --online``` - Get the list of the official WSL source images we can use to create our local WSL Distributions
- ```wsl --install -d Debian``` - Install the new local WSL Distributions from the remote official WSL source image.
- ```wsl --export Debian D:\Polygon\Learn\WSL\Debian.tar``` - Backup the current state of our WSL Distribution to the local directory.
- ```wsl --import Debian-VSBig D:\Polygon\Learn\WSL\VSBig .\Debian.tar``` - Restore the particular WSL Distribution version to the new separated instance.
- ```wsl --import Debian-VSCode D:\Polygon\Learn\WSL\VSCode .\Debian.tar``` - Restore the particular WSL Distribution version to the new separated instance.

## Some of Linux Commands
The commands I use in the job to set up some initial substances inside of the WSL Distributions are:
- ```sudo apt update``` - Actualise the index of system updater;
- ```sudo apt upgrade -y``` - Actualise the system software;
- ```sudo apt install openssh-client bash-completion``` - Install a useful tool to make you interaction with the command line more useful.



## Creating the WSL distribution of the desired type
There are a lot of templates for WSL distributions that we can use, as official and as custom. We can name many different reasons for choosing, like customer requirements, image size, target platform performance, etc. But this is not the point of this article. As a requirement for this article, we have, for instance, the **Debian** image as an initial image template. At least it is a very compact version of Linux (according to [1]) - it requires 93.5 Mb to download instead of 608 Mb of Ubuntu; it can be important when you use a metered connection. Also, Debian gets 508 MB of disk space, while Ubuntu wants 7.7 GB. So, the choice is yours.

Before creating our WSL distribution, we must see that we haven't one with a name that conflicts with our future instance.
To do that, we must ask the system to show us the list of registered images:
```
wsl --list --all
```
If we get something here, we must uninstall unnecessary instances, rename necessary instances, or plan an alternative name for our WSL distribution. The good practice is not to use default names like "Debian" or "Ubuntu" on the run. Once we create something with a default name (by the design of tools we have to use), we must rename them to our custom names. That's how we avoid some name collisions in the future.




```

```



```

```


## Reference List
- [[I] Microsoft training course - Training – Introduction to Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/training/modules/wsl-introduction)

