# postgres

```bash
mkdir ~/postgres && cp ~/selfhosted/postgres/docker-compose.yml ~/postgres/docker-compose.yml

password=$(openssl rand -base64 12 | tr -dc 'A-Za-z0-9') && sed -i "s|PSW_POSTGRES|$password|g" ~/postgres/docker-compose.yml && echo $password > ~/postgres/psw_postgres
password=$(openssl rand -base64 12 | tr -dc 'A-Za-z0-9') && sed -i "s|PSW_PGADMIN|$password|g" ~/postgres/docker-compose.yml && echo $password > ~/postgres/psw_pgadmin

mkdir -p ~/postgres/data
mkdir ~/postgres/pgadmin && sudo chown 5050:5050 ~/postgres/pgadmin
docker compose up -d
```
