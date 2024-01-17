# Config

Before all

```shell
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y git zsh curl libfuse2
git config --global user.name "Przemyslaw Papla"
git config --global user.email "przemekpapla@gmail.com"
```

- [ ] Install [IDEA Tollbox](https://www.jetbrains.com/lp/toolbox/)
- [ ] Add SSH key to your [GitHub](https://github.com/settings/keys)
- [ ] Add SSH key to your [GitLab](https://gitlab.com/-/profile/keys)
- [ ] Add SSH to your [JetBrains Space](https://ppapla.jetbrains.space/m/Porok12/authentication?tab=GitKeys)


```shell
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

```shell
cd ~
git clone git@github.com:Porok12/config.git
```

## Use

See https://www.atlassian.com/git/tutorials/dotfiles

```shell
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
echo ".cfg" >> .gitignore
git clone --bare <git-repo-url> $HOME/.cfg
config checkout
config config --local status.showUntrackedFiles no
```

## NVM https://github.com/nvm-sh/nvm

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```


