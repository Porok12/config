# Config

Before all

```shell
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y git zsh curl fzf jq vim libfuse2 ca-certificates gnupg nmap python3-pip
git config --global user.name "Przemyslaw Papla"
git config --global user.email "przemekpapla@gmail.com"
ssh-keygen
```

- [ ] Install [IDEA Tollbox](https://www.jetbrains.com/lp/toolbox/)
- [ ] Add SSH key to your [GitHub](https://github.com/settings/keys)
- [ ] Add SSH key to your [GitLab](https://gitlab.com/-/profile/keys)
- [ ] Add SSH to your [JetBrains Space](https://ppapla.jetbrains.space/m/Porok12/authentication?tab=GitKeys)


```shell
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
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

## SDKMAN https://sdkman.io/

```shell
curl -s "https://get.sdkman.io" | bash
```

## DOCKER https://docs.docker.com/engine/install/ubuntu/

```shell
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

## PODMAN https://podman.io

TODO

## K8S

```shell
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update && sudo apt-get install -y kubectl
# snap install kubectl --classic
```

```shell
sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
sudo ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx
sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens

# ahmetb/kubectx path:completion kind:fpath ?

# mkdir -p ~/.oh-my-zsh/custom/completions
#chmod -R 755 ~/.oh-my-zsh/custom/completions
#ln -s /opt/kubectx/completion/_kubectx.zsh ~/.oh-my-zsh/custom/completions/_kubectx.zsh
#ln -s /opt/kubectx/completion/_kubens.zsh ~/.oh-my-zsh/custom/completions/_kubens.zsh
#echo "fpath=($ZSH/custom/completions $fpath)" >> ~/.zshrc
```

```shell
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update && sudo apt-get install -y helm
# sudo snap install helm --classic
```

```shell
export KUBECM_VERSION=0.27.1
curl -Lo kubecm.tar.gz https://github.com/sunny0826/kubecm/releases/download/v${KUBECM_VERSION}/kubecm_v${KUBECM_VERSION}_Linux_x86_64.tar.gz
tar -zxvf kubecm.tar.gz kubecm
sudo mv kubecm /usr/local/bin/
```

```shell
sudo snap install k9s
```

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

```shell
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt-get install -y terraform
```

## CLI

```shell
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update && sudo apt install -y gh

# https://gitlab.com/gitlab-org/cli/-/blob/main/README.md#installation

curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
sudo apt-get update && sudo apt-get install -y google-cloud-cli
```

```shell
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install -y vlt
```

## Other

```shell
sudo apt-get install -y webp-pixbuf-loader
sudo apt-get install -y speech-dispatcher
sudo apt-get install -y fonts-powerline
# https://keystore-explorer.org/downloads.html
```
