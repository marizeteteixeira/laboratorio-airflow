- terminal
```shell
docker compose -f docker/docker-compose.yml exec webserver bash
```
- no container
```shell
airflow users create \
    --username admin \
    --firstname Firstname \
    --lastname Lastname \
    --role Admin \
    --email admin@example.com \
    --password admin
```

