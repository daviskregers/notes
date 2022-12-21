This is something very old. Consider using [[ansible]] instead.

```
# Show Hidden files
defaults write com.apple.finder AppleShowAllFiles YES
killall Finder

# Install powerline fonts for zsh theme
cd /tmp
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
cd ..\
rm -rf fonts

# Iterm2, homebrew, node.js, java

ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
brew update
brew install node
brew cask install appcleaner
brew cask install iterm2
curl -L https://iterm2.com/shell_integration/install_shell_integration_and_utilities.sh | bash

sudo xcodebuild -license

# JAVA
brew tap caskroom/versions
brew cask install java8
touch ~/.android/repositories.cfg
brew cask install android-sdk

# SUBLIME 3
brew install caskroom/cask/brew-cask
brew tap caskroom/versions
brew cask install sublime-text

# DOCKER 

brew install bash-completion
brew cask install docker
brew install kubectl
brew cask install minikube

# Apps
brew cask install google-chrome
brew cask install firefox
brew cask install anaconda
brew cask install dropbox
brew cask install microsoft-office
brew cask install spotify
brew cask install qt-creator
brew cask install sourcetree
brew cask install lepton
brew cask install transmit4
brew cask install sequel-pro
brew cask install mamp
brew cask install slack
brew cask install resolutionator
brew install caskroom/cask/flux
brew cask install telegram
brew cask install phpstorm
brew cask install pycharm
brew cask install imageoptim
brew install imageoptim-cli

# Apps from appstore
brew install mas
mas install 478570084
mas install 853824330
mas install 960276676
mas install 409201541
mas install 409183694
mas install 1120214373
mas install 425424353
mas install 409203825
mas install 497799835

brew install zsh zsh-completions
```
