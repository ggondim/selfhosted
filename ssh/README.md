# ssh

```bash
cp ~/selfhosted/ssh/id_rsa.gpg ~/.ssh/id_rsa.gpg
gpg -d ~/.ssh/id_rsa.gpg > ~/.ssh/id_rsa

cp ~/selfhosted/ssh/config.gpg ~/.ssh/config.gpg
gpg -d ~/.ssh/config.gpg > ~/.ssh/config

sudo chmod 600 ~/.ssh/id_rsa
sudo chmod 777 ~/.ssh
```

## if problems with ssh key - ubuntu

```bash
sudo apt install tofrodos
frodos dos2unix ~/.ssh/id_rsa -f
vi --clean ~/.ssh/id_rsa
```
