# Airflow 2.0 with Docker in Synology NAS

This is taken from [Apache/Airflow](https://github.com/apache/airflow) because I couldn't get the current version to work in Synology NAS.

Before you start, you should try out the steps from [Airflow website](https://airflow.apache.org/docs/apache-airflow/stable/start/docker.html) to check if their newer method works. Mine didn't, so I created this so that I can reproduced the steps later.

## Quick Start

- Ssh into Synology NAS
- Go to Docker folder, i.e. `/volume1/docker/` and create a folder `docker-airflow`
- Download and copy the `docker-compose.yaml` file to that folder
- Initialize the environment

```
mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)" > .env
```

- Initialize the database 

```
docker-compose up airflow-init
```

After you are done, you should see similar message like below

```
airflow-init_1       | Upgrades done
airflow-init_1       | Admin user airflow created
airflow-init_1       | 2.2.5
start_airflow-init_1 exited with code 0
```

- Once done, run following command and wait for the docker containers to be created.

```
docker-compose up -d
```

__Note:__ Likely need to run with root access, therefore need to add `sudo` in front for all docker commands.
