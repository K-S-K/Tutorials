# VSCode on Ubuntu

https://code.visualstudio.com/docs/cpp/introvideos-cpp


#### Intro steps:
- [C/C++ for Visual Studio Code](https://code.visualstudio.com/docs/languages/cpp)
- [Get started with CMake Tools on Linux](https://code.visualstudio.com/docs/cpp/cmake-linux)
- 
- [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- [Introduction to Git in VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)
- [Working with GitHub in VS Code](https://code.visualstudio.com/docs/sourcecontrol/github)
- 

#### WiFi adapter
- [Restarting after driver update](https://forums.linuxmint.com/viewtopic.php?t=331246)
```
sudo service network-manager restart
```
- [Get the WiFi adapter type (and some commands around ("Installing Broadcom Wireless Drivers")](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
```
lspci -nn -d 14e4:
```
The answer is: **Network controller [0280]: Broadcom Inc. and subsidiaries BCM43228 802.11a/b/g/n [14e4:4359]**
- [Identifying Your Broadcom BCM43xx Chipset](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
```
lspci -vvnn | grep -A 9 Network
```
The answer is:
```
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43228 802.11a/b/g/n [14e4:4359]
	Subsystem: Lite-On Communications Inc BCM43228 802.11a/b/g/n [11ad:6603]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at b3400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: bcma, wl
```
- [broadcom-sta-dkms_6.30.223.271-17_all.deb](https://ubuntu.pkgs.org/22.04/ubuntu-multiverse-arm64/broadcom-sta-dkms_6.30.223.271-17_all.deb.html) -> download http://ports.ubuntu.com/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-17_all.deb
- Online installation:
```
sudo apt-get install broadcom-sta-dkms
```
- Downloaded **deb** package installation:
```
sudo apt install ./broadcom-sta-dkms_6.30.223.271-17_all.deb
```




#### Useful things for VSCode:
- You can format an entire file with Format Document (_**Ctrl+Shift+I**_) 


#### Useful things for Command Line
- How to run a program (server) from the command line and still be able to work on the command line while it runs.<br>It must be & after the command.
```
./server &
```
- How to list processes sorted by Process ID
```
ps -e
```
- How to list processes sorted by Process Name
```
ps -e --sort=cmd
```
- How to know what program is listening on a given port
```
lsof -i :8080
```
- How to list all network connections
```
sudo netstat -nlp
```
