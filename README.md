# pgsql and pgadmin
I use it for virtual environment when I need run Postgres SQL and PG Admin. In my case I use Ubuntu server 20.04.

## Prerequisites
1. [Git](https://git-scm.com/downloads)
2. [Docker](https://docs.docker.com/desktop/)

## How to use
1. From terminal clone git-repo: ``git clone https://github.com/lobanov4real/pgsql-pgadmin.git``
2. Go to repo folder: ``cd ./pgsql-pgadmin``
3. Fill variable values in **.env** file.
4. Run docker-compose: ``docker-compose up -d``
5. From host open browser and go to PG Admin: http://<ip_of_docker_server> and use values from $PG_EMAIL and $PG_PASSWORD for login into PG Admin console.
