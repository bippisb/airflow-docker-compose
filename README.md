# Apache Airflow Deployment with Docker Compose
This project is a solution for setting up Apache Airflow using Docker Compose. It provides a simple and easy way to get started with Apache Airflow.This repository contains a Docker Compose file and an environment file for deploying Apache Airflow using Docker containers. The deployment consists of four services: postgres, scheduler, webserver, and airflow-init.

## Prerequisites
 - Docker and Docker Compose installed on your machine.
## Setting up the project
- Clone the project repository to your local machine.
- Navigate to the project directory in your terminal.
- Run the following command to start the services:
## Windows Installation

```bash
git clone https://github.com/bippisb/airflow-docker-compose.git
cd airflow-docker-compose
md dags
md logs
md plugins
docker build . -f Dockerfile --pull --tag airflow-ext:0.0.1
docker compose up -d
```
The Airflow UI will be available at http://localhost:8080. The logs and DAGs directories are mapped to the host machine, allowing you to persist the logs and DAGs across restarts of the containers. The plugins directory can be used to extend the functionality of Airflow.
## Note
- The default username and password are both set to airflow.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)
