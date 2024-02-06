# Windows Subsystem for Linux

## Abstract
Sometimes, we need to create some elementary things to provide a proper environment for a project. As we don't perform these things every day, we can forget some details, and we'll be forced to spend nights googling them. It is better to have the short form of the information in an understandable form.

## Introduction
The article covers several tiny activities:
- Basic WSL commands;
- Creating the WSL distribution of the desired type;
- Accessing the working WSL distribution command line;
- Creating the restore points of the WSL distribution instance;
- Creating the clones of the distribution for different experiments.

The use case of the article is to create two particular WSL Distributions cloned from one source WSL Distribution, to use them later in the experiments with Visual Studio and with Visual Studio Code.

## Commands
So we go Linux, and it's time to make steps from UI-centric life to the world of commands. We will use commands in Windows Console, and we will also write some commands into the Linux subsystem via Windows Terminal. But before we go, let's see all the commands we will use in our experiments.

### Some of the Basic WSL Commands
There are perfect and detailed descriptions of most WSL commands at the official site[^ms-learn-basic]. This article does not contain all of them.
The commands I use in the job, described in the article, are:
- ```wsl --list --all -v``` - Get the list of WSL Distributions we have registered on the local machine
- ```wsl --list --online``` - Get the list of the official WSL source images we can use to create our local WSL Distributions
- ```wsl --install -d <Online-WSL-Distribution-Image-Name>``` - Install the new local WSL Distributions from the remote official WSL source image.
- ```wsl --export <Local-WSL-Distribution-Name> <Local-Storage-Path\WSL-Archieve-Name>``` - Backup the current state of our WSL Distribution to the local directory.
- ```wsl --import <New-WSL-Name> <New-WSL-Working-Directory-Path> <Local-Storage-Path\WSL-Archieve-Name>``` - Restore the particular WSL Distribution version to the new separated instance.
- ```wsl --distribution <Local-WSL-Distribution-Name>``` - Run the WSL distribution specified by name.
- ```wsl --terminate <WSL Distribution Name>``` - Run the WSL distribution specified by name.
- ```wsl --shutdown``` - Immediately terminates all running distributions and the WSL utility virtual machine.

### Some of Linux Commands
The commands I use in the job to set up some initial substances inside of the WSL Distributions are:
- ```sudo apt update``` - Actualise the index of system updater;
- ```sudo apt upgrade -y``` - Actualise the system software;
- ```sudo apt install openssh-client bash-completion``` - Install a useful tool to make your interaction with the command line more useful.

## Experimental part

### Creating the WSL distribution of the desired type
There are a lot of templates for WSL distributions that we can use, as official and as custom. We can name many reasons for choosing, like customer requirements, image size, target platform performance, etc. But this is not the point of this article. As a requirement for this article, we have, for instance, the **Debian** image as an initial image template. At least it is a very compact version of Linux (according to [^1]) - it requires 93.5 Mb to download instead of 608 Mb of Ubuntu; it can be important when you use a metered connection. Also, Debian gets 508 MB of disk space, while Ubuntu wants 7.7 GB. So, the choice is yours.

### Get the name of the source image we can use as the initial template
```
wsl --list --online
```
From this list, we can copy the exact name of the initial source and see the new possibility they added for us to use. Let it be the "Debian" for our experiments.


### Check the initial state
Before creating our WSL distribution, we must see that we haven't one with a name that conflicts with our future instance.
To do that, we must ask the system to show us the list of registered images:
```
wsl --list --all
```
Suddenly, the system wants to name a new WSL distribution with the name of the source image. We can't change this flow, so we must adapt it to be compatible with what we have to deal with.

If we get something confusing us here, we must uninstall unnecessary instances, rename necessary instances, or plan an alternative name for our WSL distribution. The good practice is not to use default names like "Debian" or "Ubuntu" on the run. Once we create something with a default name (by the design of tools we have to use), we must rename them to our custom names. That's how we avoid some name collisions in the future.
**TODO: Research the system behavior here.**

### Create a new, clean image of the WSL distribution
```
wsl --install -d Debian
```
Indeed, instead of Debian, you can use the name of the source image you need to use for your purposes.
While performing this task, WSL will download the system image from the hosting site, deploy it on your system, and run it. It can take some time, depending on the size of the selected image and your connection speed. When the deployment is complete, you will be prompted to enter your name and password.


### Make some of your task-specific preparations
When you see the Linux command prompt, you can perform some housekeeping things to make your base image more ready-to-use, which can be out-of-box. Sure, you can call here any housekeeping commands which are specific to your tasks.
```
sudo apt update
```
```
sudo apt upgrade -y
```
```
sudo apt install openssh-client bash-completion
```

### Prepare your local WSL distribution template image
Now, we can create an archive copy of our WSL distribution. We can use it as a template for creating our experimental WSL distributions or as restore points for tests or experiments. We need to decide which directory we will use to store the images and the name of our image template. The WSL creates tar archives of the distributions. We can use the command to do that:
```
wsl --export Debian D:\Polygon\Learn\WSL\Debian.tar
```
Now, we can go to Windows Explorer, Far, or whatever you use to see the archive WSL created for us. We can keep it, make copies, etc.


### Create a new WSL distribution from the local archive
Now, we can create as many copies of our WSL distribution as we need. To do that, we must know three things.
1. The path to our WSL template archive;
2. The directory where WSL distribution will be locally deployed;
3. The name of our new WSL distribution instance (yes, now we have a parameter to name it).

```
wsl --import Debian-VSBig D:\Polygon\Learn\WSL\VSBig .\Debian.tar
```
```
wsl --import Debian-VSCode D:\Polygon\Learn\WSL\VSCode .\Debian.tar
```

With these two commands, I've created two instances of our template WSL distribution to make all the experiments I want to perform with them.


## Conclusion
Now, we have an approach to running and debugging some Linux-specific tasks from the Windows development environment. More interesting things you can see in the Microsoft training course [^I].


## Reference List
[^1]: [Installing Debian on Windows 10/11 using WSL from the command line](https://feriman.com/installing-debian-on-windows-1011-using-wsl-from-the-command-line/)
[^ms-learn-basic]: [Basic commands for WSL at learn.microsoft.com](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)
[^I]: [Microsoft training course - Training – Introduction to Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/training/modules/wsl-introduction)

