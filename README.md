# how-to-setup-windows

## Windows
```powershell
Set-ExecutionPolicy Bypass -Scope Process

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

choco install firefox -y

choco install git.install vscode cursoride docker-desktop  -y

wsl --install -d Ubuntu
wsl --set-default-version 2

Restart-Computer
```
## Linux
### Tools
```shell
sudo apt update && sudo apt upgrade -y && sudo apt autoremove

sudo apt install zsh curl wget tree bat zip unzip tar git gpg make build-essential gcc -y

```
### Go
```shell
wget https://dl.google.com/go/go1.24.0.linux-amd64.tar.gz 
#sudo rm -rf ~/go ~/.go
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xvf go1.24.0.linux-amd64.tar.gz

export GOROOT=/usr/local/go >> ~/.zshrc
export GOPATH=$HOME/go >> ~/.zshrc
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH >> ~/.zshrc
source ~/.zshrc
rm go1.24.0.linux-amd64.tar.gz

go version
```
