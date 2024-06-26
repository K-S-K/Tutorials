# Ubuntu Installation Process


## [Autoconnect Bluetooth Device](https://askubuntu.com/questions/1450242/autoconnect-bluetooth-keyboard)
<details>
<summary>Expand</summary>
First, open Bluetooth settings and note the Bluetooth address of the device <br>(6 pairs of hexadecimal digits separated by colons, e.g. 70:F0:87:22:72:8E).

Enter command:
```
bluetoothctl
```

Enter the device's Bluetooth address:
```
trust 70:F0:87:22:72:8E
```

When the system confirms that it now trusts the device, enter exit:
```
exit
```

The next time you start, the device will connect automatically.
</details>



## Install software after system
- ### [Install JetBrains Mono Fonts](https://www.jetbrains.com/lp/mono/)
- ### [Install Google Chrome](google.com/chrome)
- ### [Install docker](https://docs.docker.com/engine/install/ubuntu/)
<details>

<summary>Bash script</summary>

```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
</details>


- ### [Make Docker Commands executable without sudo](https://medium.com/devops-technical-notes-and-manuals/how-to-execute-docker-commands-without-sudo-in-ubuntu-22-04-command-line-tutorial-3d0f24aefbf7):

<details>

<summary>Execute the commands:</summary>

- Check if Docker itself is working
```
sudo docker run hello-world
```

- Check if Docker does not work without sudo
```
sudo docker images
```

- Add the docker group (it might already exist):
```
sudo groupadd docker
```

- Add the connected user “$USER” to the docker group
```
sudo gpasswd -a $USER docker
```

- Activate the changes to group
```
newgrp docker
```

- Test the result
```
sudo docker images
```
</details>

- ### Install git
```
sudo apt install git
```

- ### Install Github Desktop
```
wget -qO - https://apt.packages.shiftkey.dev/gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/shiftkey-packages.gpg > /dev/null
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/shiftkey-packages.gpg] https://apt.packages.shiftkey.dev/ubuntu/ any main" > /etc/apt/sources.list.d/shiftkey-packages.list'
sudo apt update && sudo apt install github-desktop
```


- ### Install Docker Buildx service
```
sudo apt install docker-buildx
```

- ### Install Docker Compose
```
sudo apt  install docker-compose
```

- ### Install Developer Tools
```
sudo apt-get install -y g++ make
```

- ### Install Telegram Desktop
```
sudo snap install telegram-desktop
```

- #### [Install VSCode](https://askubuntu.com/questions/616075/how-do-i-install-visual-studio-code)
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EB3E94ADBE1229CF
sudo add-apt-repository -y "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt -y install code
```

- #### [Install MPLAB](https://forum.microchip.com/s/topic/a5C3l000000MZEDEA4/t365477)
- - Download and extract MPLAB IDE installer for Linux
  - Make it executable
```
chmod u+x MPLABX-v6.20-linux-installer.sh
```
  - Install this thing:
```
sudo apt-get install libc6:i386 libx11-6:i386 libxext6:i386 libstdc++6:i386 libexpat1:i386
```
  - Execute installer
```
sudo ./MPLABX-v6.20-linux-installer.sh
```


- #### Install MPEG-4 AAC decoder, and the H.264 decoder
```
sudo apt-get install ubuntu-restricted-extras
```


- ### [Check Bluetooth devices battery status](https://askubuntu.com/questions/1117563/)
```
upower --dump

```

<summary>Configure Ubuntu for Git SSH</summary>
<details>

#### The configuration steps:
- Read [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/enterprise-cloud@latest/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Read [Adding a new SSH key to your GitHub account](https://docs.github.com/en/enterprise-cloud@latest/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- ```cd /home/ksk/.ssh``` - Go to the directory where SSH keys are
- ```ssh-keygen -t ed25519 -C "yourname@gmail.com"``` - Create key (specify key file name and password for the key
- ```ls -al``` - See new key files
- ```eval "$(ssh-agent -s)"``` - Ensure that agent is working
- ```ssh-add ~/.ssh/keyfilename``` - Register the key
- ```cat keyfilename``` - Copy keys to GitHub, or
- ```
- Go to [your GitHub SSH keys](https://github.com/settings/keys) and register your key
- ```git config --global user.email "yourname@gmail.com"``` - Configure your email
- ```git config --global user.name "Stanislav Kiselevskii"``` - Configure your Name and Last Name
- ```pbcopy < ~/.ssh/keyname.pub``` - copy the key to the clipboard
- [edit SSH config file](https://stackoverflow.com/questions/54133300/how-to-access-and-modify-a-ssh-file-on-mac)
- ```git config pull.ff only``` - this is good
- ```git config pull.rebase true``` - not recommended
- ```git config pull.rebase false``` - not recommended
- 
- Read [Authentication Failure on Github even after adding SSH key]()https://stackoverflow.com/questions/17580261/authentication-failure-on-github-even-after-adding-ssh-key
- ```git remote -v```
- ```git remote set-url origin ssh://git@github.com/K-S-K/CCSS.git/```
- ```git remote -v```

</details>




## How to Fix SSH Failed Permission Denied


#### Server-side operations: 
https://phoenixnap.com/kb/ssh-permission-denied-publickey
```
sudo nano sshd_config
```
Modify parameters:
- PasswordAuthentication yes
- KbdInteractiveAuthentication yes


#### Client-side operations:

Create key

Copy key to the server:
```
ssh-copy-id -i ~/.ssh/rpi-gm-ki.pub -p22 ksk@KSK-PI3B
```

Connect the server:
```
ssh -v ksk@KSK-PI3B
```

#### Other materials:
- [How to create a sudo user on Ubuntu and allow SSH login](https://thucnc.medium.com/how-to-create-a-sudo-user-on-ubuntu-and-allow-ssh-login-20e28065d9ff)
- [How to fix Permission Denied (Public key) error](https://askubuntu.com/questions/337757/how-to-fix-permission-denied-public-key-error)
- [Easiest way to copy ssh keys to another machine](https://askubuntu.com/questions/4830/easiest-way-to-copy-ssh-keys-to-another-machine)
- [Copy the ssh key into remote servers](https://medium.com/@anshulganvir/copy-the-ssh-key-into-remote-servers-3416f13cca47)
- [How to configure ssh client to use private keys automatically](https://serverfault.com/questions/262626/how-to-configure-ssh-client-to-use-private-keys-automatically)
- [How to set up an SSH config-file for beginners](https://stackoverflow.com/questions/56287059/how-to-set-up-an-ssh-config-file-for-beginners)
- [Configure ssh to use the key](https://askubuntu.com/questions/311558/ssh-permission-denied-publickey)




## 3.2" DISPLAY

https://www.waveshare.com/wiki/3.2inch_RPi_LCD_(B)

https://github.com/waveshare/LCD-show

https://www.waveshare.com/3.2inch-rpi-lcd-b.htm




## References
- [Where to install bootloader when installing Ubuntu as secondary OS](https://askubuntu.com/questions/219514/where-to-install-bootloader-when-installing-ubuntu-as-secondary-os)
- [Select device boot installation for installing Ubuntu dual boot with Windows 10](https://askubuntu.com/questions/1314321/select-device-boot-installation-for-installing-ubuntu-dual-boot-with-windows-10)
- [How to Enable Hibernate Function in Ubuntu 22.04 LTS](https://askubuntu.com/questions/1240123/how-to-enable-the-hibernate-option-in-ubuntu-20-04)
- [How to Enable Hibernate Function in Ubuntu 22.04 LTS](https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/)
