# ubuntu

## netplan problems

```bash
sudo apt install -y net-tools
sudo mv ~/selfhosted/ubuntu/50-cloud-init.yaml /etc/netplan/50-cloud-init.yaml
sudo chown root:root /etc/netplan/50-cloud-init.yaml
sudo chmod 644 /etc/netplan/50-cloud-init.yaml
sudo netplan apply
```

## basic setup commands

```bash
sudo unminimize -y
```

```
sudo apt update && sudo apt upgrade -y && sudo apt install -y build-essential curl git vim
```

### ssh & neofetch


```bash
sudo cp ~/selfhosted/ubuntu/sshd_config /etc/ssh/sshd_config
sudo sed -i 's/USERNAME/'$USER'/g' /etc/ssh/sshd_config
sudo chmod 644 /etc/ssh/sshd_config
sudo systemctl restart ssh
```

```bash
sudo apt install -y neofetch
cd /etc/update-motd.d && sudo chmod 200 00-header 10-help-text 50-motd-news 91-contract-ua-esm-status
sudo mv ~/selfhosted/ubuntu/02-neofetch /etc/update-motd.d/02-neofetch && sudo chmod 755 /etc/update-motd.d/02-neofetch
```

### install docker

```bash
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt update && sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin && sudo docker run hello-world

# Add user to docker group
sudo groupadd docker
sudo usermod -aG docker $USER
exit
docker run hello-world

# lazydocker
curl https://raw.githubusercontent.com/jesseduffield/lazydocker/master/scripts/install_update_linux.sh | bash

echo "alias lzd='lazydocker'" >> ~/.profile && source ~/.profile

lzd
```

# a single network to rule them all

```bash
docker network create local-internal
```
