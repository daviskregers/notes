# Mint installation

## setup

```
RED='\033[0;31m'
NC='\033[0m' # No Color

echo -e "${RED} Updating system packages ... ${NC}"
sudo apt update && sudo apt upgrade -y
sudo apt install -y pv

### Chrome

echo -e "${RED} Installing Google Chrome ... ${NC}"

wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | sudo tee /etc/apt/sources.list.d/google-chrome.list
sudo apt update 
sudo apt install --fix-broken -y google-chrome-stable

### Dropbox

echo -e "${RED} Installing Dropbox ...${NC}"
sudo apt install --fix-broken dropbox

### Spotify

echo -e "${RED} Installing Spotify ...${NC}"

sudo rm /etc/apt/sources.list.d/spotify.list

sudo sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list.d/spotify.list'
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0DF731E45CE24F27EEEB1450EFDC8610341D9410
sudo apt-get update
sudo apt-get install spotify-client

echo -e "${RED} Installing GIT ...${NC}"

sudo apt install --fix-broken liberror-perl git-man git -y

echo -e "${RED} Installing Boostnote ...${NC}"

'
cd /tmp
wget https://github.com/BoostIO/boost-releases/releases/download/v0.11.10/boostnote_0.11.10_amd64.deb
sudo dpkg -i boostnote_0.11.10_amd64.deb
'

echo -e "${RED} Installing Visual Studio Code ...${NC}"

'
cd /tmp
sudo apt install software-properties-common apt-transport-https wget -y
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt install code -y
'

echo -e "${RED} Installing Wine ...${NC}"

cd /tmp
sudo dpkg --add-architecture i386
wget -nc https://dl.winehq.org/wine-builds/Release.key
sudo apt-key add Release.key
sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
sudo apt update
sudo apt install wine-stable winehq-stable -y

echo -e "${RED} Installing HeidiSQL ... be sure to enable https://github.com/HeidiSQL/HeidiSQL/issues/83#issuecomment-375969129 afterwards ${NC}"

cd /tmp
wget https://www.heidisql.com/builds/heidisql64.r5317.exe
chmod +x heidisql64.r5317.exe
./heidisql64.r5317.exe

echo -e "${RED} Installing Docker ...${NC}"

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt-get update
sudo apt-get install -y docker-ce
sudo systemctl status docker
sudo usermod -aG docker ${USER}
docker -v

sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

echo -e "${RED} Installing Git Kraken ...${NC}"

cd /tmp
sudo apt install libgnome-keyring-common libgnome-keyring-dev -y
wget https://release.gitkraken.com/linux/gitkraken-amd64.deb
sudo dpkg -i gitkraken-amd64.deb

echo -e "${RED} Installing Slack ...${NC}"

sudo apt install snapd
sudo snap install slack --classic

echo -e "${RED} Installing Discord ...${NC}"

sudo apt install libgconf-2-4 libappindicator1
sudo snap install discord

echo -e "${RED} Installing Guake ...${NC}"

sudo apt install guake -y

echo -e "${RED} Installing ZSH ...${NC}"

sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

git clone https://github.com/tarjoilija/zgen.git "${HOME}/.zgen"

sudo apt-get install fonts-powerline

echo -e "${RED} Installing F.LUX ...${NC}"

sudo add-apt-repository ppa:nathan-renniewaldock/flux
sudo apt-get update
sudo apt-get install fluxgui

echo -e "${RED} Installing Shutter ...${NC}"

sudo apt install shutter -y

echo -e "${RED} Installing Postman ...${NC}"

apt-get install libgconf-2-4 -y
cd /tmp
wget https://dl.pstmn.io/download/latest/linux64 -O postman.tar.gz
sudo tar -xzf postman.tar.gz -C /opt
rm postman.tar.gz
sudo ln -s /opt/Postman/Postman /usr/bin/postman
cat > ~/.local/share/applications/postman.desktop <<EOL
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=postman
Icon=/opt/Postman/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
EOL

echo -e "${RED} Cleanup ...${NC}"

sudo apt autoremove -y
```