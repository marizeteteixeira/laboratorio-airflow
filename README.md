# Laboratório Airflow

Este repositório contém uma configuração do Apache Airflow utilizando Docker e Docker Compose, com integração ao MySQL para armazenamento de dados. O projeto inclui DAGs de exemplo para ingestão de dados a partir de uma API pública e armazenamento no banco de dados MySQL.

## Estrutura do Projeto

```
laboratorio-airflow/
├── dags/
│   └── __init__.py
├───── aula_airflow/
│      └── __init__.py
├── docker/
│   ├── Dockerfile
│   └── docker-compose.yml
├── .env
├── poetry.lock
├── pyproject.toml
├── requirements.txt
└── README.md
```

## Inicializar o Ambiente

Para inicializar o serviço, utilize o comando:

```shell
docker compose -f docker/docker-compose.yml up --build
```

## Criar o Usuário para Fazer Login no Airflow

Após inicializar o serviço, crie um usuário admin para acessar a interface do Airflow:

1. Acesse o container do webserver:

```shell
docker compose -f docker/docker-compose.yml exec webserver bash
```

2. No container, crie o usuário admin:

```shell
airflow users create \
    --username admin \
    --firstname Firstname \
    --lastname Lastname \
    --role Admin \
    --email admin@example.com \
    --password admin
```

## Configurar a Conexão MySQL no Airflow

1. Acesse a interface do Airflow em [http://localhost:8080](http://localhost:8080) e faça login com as credenciais criadas.
2. Vá para `Admin` -> `Connections`.
3. Clique em `+` para adicionar uma nova conexão e configure os campos conforme abaixo:

- **Conn Id**: `mysql_default`
- **Conn Type**: `MySQL`
- **Host**: `mysql`
- **Schema**: `airflow`
- **Login**: `airflow`
- **Password**: `airflow`
- **Port**: `3306`

## Monitoramento de Logs

Certifique-se de que a configuração acima esteja correta para evitar problemas de acesso aos logs.

## Licença

Este projeto é licenciado sob os termos da licença MIT.
