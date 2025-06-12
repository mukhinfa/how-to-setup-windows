# how-to-setup-windows

## Windows
```powershell
#Run in PowerShell as Administrator
#install choco
Set-ExecutionPolicy Bypass -Scope Process

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
#system
choco install vcredist140 vcredist2015 vcredist2010 vcredist2008 vcredist2017 vcredist2013 -y
#browser
choco install firefox googlechrome -y
#development
choco install git.install vscode cursoride docker-desktop dbeaver virtualbox postman -y

#other
choco install vlc audacity obs-studio.install sumatrapdf qbittorrent fsviewer zoom -y

wsl --install -d Ubuntu
wsl --set-default-version 2

Restart-Computer
```
## Linux
### Tools
```shell
sudo apt update && sudo apt upgrade -y && sudo apt autoremove

sudo apt install zsh curl wget tree bat zip unzip tar git gpg make build-essential gcc ripgrep -y

```
#### zsh
```shell
sudo apt install powerline fonts-powerline
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
nano ~/.zshrc
```
change theme
```shell
ZSH_THEME="agnoster"
```
Syntax Highlighting
```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "$HOME/.zsh-syntax-highlighting" --depth 1
echo "source $HOME/.zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> "$HOME/.zshrc"
```
Autosuggestions
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
nano ~/.zshrc
```
add plugin
```shell
plugins=(
    git
    z
    zsh-autosuggestions
    zsh-color-logging
    docker
    docker-compose
    history
    eza-zsh
    colorize
    command-not-found
    copyfile
    copypath
    dotenv
    golang
    gnu-utils
    iterm2
    man
    ssh
    sudo
)
```
add alias (optional)
'''shell
alias ls='eza --tree --level=1 --icons=always --no-time --color=always --no-user --no-permissions'
'''

Upd config
```shell
source ~/.zshrc
```
Set zsh as default
```shell
chsh -s /bin/zsh
```

### Go
```shell
curl -sSL https://golang.org/dl/$(curl -s https://golang.org/VERSION?m=text | head -n1).linux-amd64.tar.gz -o go_latest.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xvf go_latest.tar.gz
rm go_latest.tar.gz

export GOROOT=/usr/local/go >> ~/.zshrc
export GOPATH=$HOME/go >> ~/.zshrc
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH >> ~/.zshrc
source ~/.zshrc
rm go1.24.0.linux-amd64.tar.gz

go version
```
