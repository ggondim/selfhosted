# n8n

```bash
mkdir ~/n8n && cp ~/selfhosted/n8n/docker-compose.yml ~/n8n/docker-compose.yml
pwdredis=$(cat ~/redis/psw) && sed -i "s|PSW_REDIS|$pwdredis|g" ~/n8n/docker-compose.yml
pwdpostgres=$(cat ~/postgres/psw) && sed -i "s|PSW_POSTGRES|$pwdpostgres|g" ~/n8n/docker-compose.yml
mkdir ~/n8n/.n8n && sudo chown 1000:1000 ~/n8n/.n8n
docker compose up -d
```