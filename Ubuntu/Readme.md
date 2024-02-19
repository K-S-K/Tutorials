# VSCode on Ubuntu

https://code.visualstudio.com/docs/cpp/introvideos-cpp


## Intro steps:
- [C/C++ for Visual Studio Code](https://code.visualstudio.com/docs/languages/cpp)
- [Get started with CMake Tools on Linux](https://code.visualstudio.com/docs/cpp/cmake-linux)
- 
- [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- [Introduction to Git in VS Code](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git)
- [Working with GitHub in VS Code](https://code.visualstudio.com/docs/sourcecontrol/github)
- 


## Makefile tutorials
- [Learn Makefiles With the tastiest examples](https://makefiletutorial.com/)
- [GNU make](https://www.gnu.org/software/make/manual/make.html)

## WiFi adapter
<details>

<summary>All attempts information is here</summary>

#### [Restarting after driver update](https://forums.linuxmint.com/viewtopic.php?t=331246)
```
sudo service network-manager restart
```
#### [Get the WiFi adapter type (and some commands around ("Installing Broadcom Wireless Drivers")](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
```
lspci -nn -d 14e4:
```
The answer is: **Network controller [0280]: Broadcom Inc. and subsidiaries BCM43228 802.11a/b/g/n [14e4:4359]**
#### [Identifying Your Broadcom BCM43xx Chipset](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
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
#### [broadcom-sta-dkms_6.30.223.271-17_all.deb](https://ubuntu.pkgs.org/22.04/ubuntu-multiverse-arm64/broadcom-sta-dkms_6.30.223.271-17_all.deb.html) -> download http://ports.ubuntu.com/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-17_all.deb
- Online installation:
```
sudo apt-get install broadcom-sta-dkms
```
- Downloaded **deb** package installation:
```
sudo apt install ./broadcom-sta-dkms_6.30.223.271-17_all.deb
```

</details>






## Useful things for VSCode:
- You can format an entire file with Format Document (_**Ctrl+Shift+I**_) 



## Useful things for Docker:
- Enter to the Docker Container session with command line
```
docker exec -it [container-id] bash
```
- [Network mode container in docker-compose](https://stackoverflow.com/questions/58102461/network-mode-container-in-docker-compose)
- [Volume configuration reference](https://docs.docker.com/compose/compose-file/compose-file-v2/#volume-configuration-reference)
- [volumes](https://docs.docker.com/compose/compose-file/compose-file-v2/#volumes)
- [network_mode](https://docs.docker.com/compose/compose-file/compose-file-v2/#network_mode)
- 
- [Can I run multiple instances of a service in docker-compose](https://stackoverflow.com/questions/73988014/can-i-run-multiple-instances-of-a-service-in-docker-compose)
- [What is a good way to run my Docker containerized application as a systemd service?](https://askubuntu.com/questions/1500625/what-is-a-good-way-to-run-my-docker-containerized-application-as-a-systemd-servi)
- 
- [Building images - Multi-stage builds](https://docs.docker.com/build/building/multi-stage/)
- [Build with Docker - Multi-stage](https://docs.docker.com/build/guide/multi-stage/)
- [How to define build-args in docker-compose](https://stackoverflow.com/questions/50734271/how-to-define-build-args-in-docker-compose)
- [How to pass --build-arg parameters from command line to docker-compose.yml file](https://stackoverflow.com/questions/60499764/how-to-pass-build-arg-parameters-from-command-line-to-docker-compose-yml-file)
- 
- [How to communicate between Docker containers via "hostname"](https://stackoverflow.com/questions/30545023/how-to-communicate-between-docker-containers-via-hostname)
- [How to establish a connection between a tcp client/server running in a Docker container and a tcp server/client running in an external device?](https://stackoverflow.com/questions/66782118/how-to-establish-a-connection-between-a-tcp-client-server-running-in-a-docker-co)



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
- How install netstat
```
apt install net-tools
```
- Manual Installation
```sudo dpkg -i package_file.deb```
```sudo apt-get remove package_name```


