# Apache Airflow Deployment with Docker Compose
This project is a solution for setting up Apache Airflow using Docker Compose. It provides a simple and easy way to get started with Apache Airflow.This repository contains a Docker Compose file and an environment file for deploying Apache Airflow using Docker containers. The deployment consists of four services: postgres, scheduler, webserver, and airflow-init.

## Services
### postgres
A PostgreSQL container used as the backend database for Airflow. It is defined with the following settings:

- Image: postgres:13
- Container name: postgres
- Exposed ports: 5434:5432
- Healthcheck: Uses pg_isready to check the health of the database
## scheduler
A container running the Airflow scheduler service, which is responsible for triggering DAG runs. It is defined with the following settings:

- Image: apache/airflow:2.3.0
- Container name: airflow-scheduler
- Command: scheduler
- Restart policy: on-failure
- Exposed ports: 8793:8793
## webserver
A container running the Airflow webserver, which provides the web interface for managing and monitoring DAGs. It is defined with the following settings:

Image: apache/airflow:2.3.0
Container name: airflow-webserver
Command: webserver
Restart policy: always
Exposed ports: 8080:8080
Healthcheck: Uses curl to check the health of the webserver
## airflow-init
A one-time container that initializes the Airflow environment by creating the necessary directories, setting the correct ownership, and verifying the version of Airflow being used. It is defined with the following settings:

- Image: apache/airflow:2.3.0
- Container name: airflow-init
- Entrypoint: /bin/bash
- Command: Runs a shell script to initialize the environment
## Environment File
The environment file (.env) contains the following variables used by the services:

- POSTGRES_USER: The username for the PostgreSQL database
- POSTGRES_PASSWORD: The password for the PostgreSQL database
- POSTGRES_DB: The name of the PostgreSQL database
- AIRFLOW__CORE__FERNET_KEY: The fernet key used to encrypt sensitive information in the database
- AIRFLOW__CORE__EXECUTOR: The executor to use for running tasks
- AIRFLOW__CORE__DAGS_ARE_PAUSED_AT_CREATION: Whether new DAGs are paused at creation
- AIRFLOW__CORE__LOAD_EXAMPLES: Whether to load example DAGs
- AIRFLOW_UID: The UID to use for the Airflow user in the containers
- AIRFLOW__DATABASE__SQL_ALCHEMY_CONN: The SQL Alchemy connection string for the database
- AIRFLOW__DATABASE__LOAD_DEFAULT_CONNECTIONS: Whether to load default connections in the database
- _AIRFLOW_DB_UPGRADE: Whether to upgrade the Airflow database
- _AIRFLOW_WWW_USER_CREATE: Whether to create the Airflow web user




## Usage
To use this Docker Compose file, simply clone this repository and run the following command in the root directory:
## Installation


```bash
git clone https://github.com/bippisb/airflow-docker-compose.git
cd airflow-docker-compose
docker-compose up -d
```
This will start the containers for each of the services defined in the file. You can then access the Airflow web interface at http://localhost:8080.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)
