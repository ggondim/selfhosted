# redis

```bash
mkdir ~/redis && cp ~/selfhosted/redis/docker-compose.yml ~/redis/docker-compose.yml
password=$(openssl rand -base64 12 | tr -dc 'A-Za-z0-9') && sed -i "s|PSSW|$password|g" ~/redis/docker-compose.yml && echo $password > ~/redis/psw
cd ~/redis && docker compose up -d
```
