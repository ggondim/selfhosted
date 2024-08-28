# mongodb

```bash
mkdir ~/mongodb && cp ~/selfhosted/mongodb/docker-compose.yml ~/mongodb/docker-compose.yml
password=$(openssl rand -base64 12 | tr -dc 'A-Za-z0-9') && sed -i "s|PSW_MONGO|$password|g" ~/mondogb/docker-compose.yml && echo $password > ~/mongodb/psw
openssl rand -base64 756 > ~/mondogb/keyfile

cd ~/mongodb && docker compose up -d

docker compose exec mongo1 mongo --eval "rs.initiate({_id: 'rs0', members: [{_id: 0, host: 'mongo1:27017'}, {_id: 1, host: 'mongo2:27018'}, {_id: 2, host: 'mongo3:27019'}]})"
```

