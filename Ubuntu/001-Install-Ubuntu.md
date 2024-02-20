# Ubuntu Installation Process


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

- ### Install Telegram Desktop
```
sudo snap install telegram-desktop
```

- ### Install git
```
sudo apt install git
```
<details>

<summary>Configure Ubuntu for Git SSH</summary>

#### The configuration steps:
- Read [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/enterprise-cloud@latest/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Read [Adding a new SSH key to your GitHub account](https://docs.github.com/en/enterprise-cloud@latest/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
- ```cd /home/ksk/.ssh``` - Go to the directory where SSH keys are
- ```ssh-keygen -t ed25519 -C "yourname@gmail.com"``` - Create key (specify key file name and password for the key
- ```ls -al``` - See new key files
- ```eval "$(ssh-agent -s)"``` - Ensure that agent is working
- ```ssh-add ~/.ssh/keyfilename``` - Register the key
- ```cat keyfilename``` - Copy keys to GitHub
- Go to [your GitHub SSH keys](https://github.com/settings/keys) and register your key
- ```git config --global user.email "yourname@gmail.com"``` - Configure your email
- ```git config --global user.name "Stanislav Kiselevskii"``` - Configure your Name and Last Name
- 
- ```git config pull.ff only``` - this is good
- ```git config pull.rebase true``` - not recommended
- ```git config pull.rebase false``` - not recommended
- 
- Read [Authentication Failure on Github even after adding SSH key]()https://stackoverflow.com/questions/17580261/authentication-failure-on-github-even-after-adding-ssh-key
- ```git remote -v```
- ```git remote set-url origin ssh://git@github.com/K-S-K/CCSS.git/```
- ```git remote -v```

</details>

- ### Install Docker Compose
```sudo apt  install docker-compose```

- ### Install Developer Tools
```apt-get install -y g++ make```





https://phoenixnap.com/kb/ssh-permission-denied-publickey

SRV: sudo nano sshd_config

CLI: ssh-copy-id -i ~/.ssh/rpi-gm-ki.pub -p22 ksk@KSK-PI3B







https://joy-it.net/en/products/RB-TFT3.2V2

https://joy-it.net/files/files/Produkte/RB-TFT3.2-V2/RB-TFT-Manual_04082020.pdf

http://www.lcdwiki.com/2.8inch_RPi_Display




## References
- [Where to install bootloader when installing Ubuntu as secondary OS](https://askubuntu.com/questions/219514/where-to-install-bootloader-when-installing-ubuntu-as-secondary-os)
- [Select device boot installation for installing Ubuntu dual boot with Windows 10](https://askubuntu.com/questions/1314321/select-device-boot-installation-for-installing-ubuntu-dual-boot-with-windows-10)
