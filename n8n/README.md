# n8n

```bash
mkdir ~/n8n && cp ~/selfhosted/n8n/docker-compose.yml ~/n8n/docker-compose.yml
pwdredis=$(cat ~/redis/psw) && sed -i "s|PSW_REDIS|$pwdredis|g" ~/n8n/docker-compose.yml

pwdpostgres=$(openssl rand -base64 16 | tr -dc 'A-Za-z0-9') && cd ~/postgres && docker compose exec postgres psql -U postgres -c "CREATE USER n8n WITH PASSWORD '$pwdpostgres';" && echo $pwdpostgres > ~/n8n/psw_postgres && sed -i "s|PSW_POSTGRES|$pwdpostgres|g" ~/n8n/docker-compose.yml

cd ~/postgres && docker compose exec postgres psql -U postgres -c "CREATE DATABASE n8n;" && docker compose exec postgres psql -U postgres -c "GRANT ALL PRIVILEGES ON DATABASE n8n TO n8n;" && docker compose exec postgres psql -U postgres -d n8n -c 'GRANT ALL ON SCHEMA public TO n8n;' && docker compose exec postgres psql -U postgres -c "GRANT ALL ON SCHEMA public TO n8n;"

mkdir ~/n8n/.n8n && sudo chown 1000:1000 ~/n8n/.n8n
cd ~/n8n && docker compose up -d
```