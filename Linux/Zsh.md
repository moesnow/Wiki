# Zsh & Oh My Zsh

> https://ohmyz.sh/

1. Debian
  `sudo apt install -y zsh git`

  Centos
  `sudo yum install -y zsh git`

2. `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

3. `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`

4. `git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`

5. `sed -i 's/(git)/(git z zsh-syntax-highlighting zsh-autosuggestions docker sudo hitokoto)/g' ~/.zshrc && source ~/.zshrc`
