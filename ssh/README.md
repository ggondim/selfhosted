# ssh

```bash
cp ~/selfhosted/ssh/id_rsa.gpg ~/.ssh/id_rsa.gpg
gpg -d ~/.ssh/id_rsa.gpg > ~/.ssh/id_rsa

cp ~/selfhosted/ssh/config.gpg ~/.ssh/config.gpg
gpg -d ~/.ssh/config.gpg > ~/.ssh/config

sudo chmod 600 ~/.ssh/id_rsa
sudo chmod 644 ~/.ssh/config
sudo chmod 600 ~/.ssh/authorized_keys
sudo chmod 700 ~/.ssh
```

## sshd

```bash
sudo cp ~/selfhosted/ubuntu/sshd_config /etc/ssh/sshd_config
sudo sed -i 's/USERNAME/'$USER'/g' /etc/ssh/sshd_config
sudo chmod 644 /etc/ssh/sshd_config
sudo systemctl restart ssh
```

## if problems with ssh key - ubuntu

```bash
sudo apt install tofrodos
fromdos ~/.ssh/id_rsa -f
vi --clean ~/.ssh/id_rsa
```
