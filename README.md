# Linux Development Setup

This simple guide lists the install commands for my development tools in Linux Ubuntu-based distros


## General
### Brave
```
sudo apt update
sudo apt install brave-browser
```

## IDEs and Development Tools
### Jetbrains Toolbox (https://www.jetbrains.com/toolbox-app/)

### Anaconda (https://docs.anaconda.com/anaconda/install/linux/)
 - Prerequisites (Debian)
 ```
sudo apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
```
 - Download installer - https://www.anaconda.com/download/#linux
 - Verify data integrity
 ```
 shasum -a 256 ~/Downloads/Anaconda3-2022.05-Linux-x86_64.sh 
 ```
 - Install
 ```
 bash ~/Downloads/Anaconda3-2022.05-Linux-x86_64.sh 
 ```
 - Accept license agreement, enter `yes` to run `conda init`
 - Refresh the terminal `sudo ~/.bashrc`
 - Creating a conda environment
 ```
 conda create --name my-env python=3.9
 ```

### Git
```
sudo apt update
sudo apt install git

git config --global user.name "Mamerto Fabian Jr"
git config --global user.email "mamerto@codefrost.com"
```

### Github CLI
```
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

### Docker Engine and Docker Desktop
```
sudo apt purge docker-desktop
sudo apt-get update
sudo apt-get install     ca-certificates     curl     gnupg     lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
sudo docker run hello-world
sudo apt-get update
sudo apt-get install ~/Downloads/docker-desktop-4.11.0-amd64.deb 

sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```
 - Set to auto start on login (optional)
 ```
 systemctl --user start docker-desktop
 ```

### NVM
```
sudo apt update && sudo apt install curl -y
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
source ~/.profile
source ~/.bashrc 
nvm ls-remote
nvm install 16
nvm list
nvm install --help
nvm -v
node -v
```

### .NET
```
sudo apt update && sudo apt install dotnet6
dotnet
```

## Others
### Hubstaff (https://app.hubstaff.com/download/linux)
```
bash ~/Downloads/Hubstaff-1.6.7-5c6fee47.sh 
```

## Customizations
### Keychron Keyboard Function Keys fix
```
echo "options hid_apple fnmode=2" | sudo tee /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```
 - Reboot
