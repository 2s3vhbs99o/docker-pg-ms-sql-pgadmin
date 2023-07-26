# pgsql, pgadmin and mssql
I use it for virtual environment when I need run Postgres SQL, PG Admin and MS SQL Express. In my case I use Ubuntu server 20.04. Cheked in last (7.3.2) [redos server](https://redos.red-soft.ru/product/downloads/) with [PostgresPro](https://hub.docker.com/r/chernoskutov/postgres-pro/).

## Prerequisites
1. [Git](https://git-scm.com/downloads)
2. [Docker](https://docs.docker.com/desktop/)

## How to use
1. From terminal clone git-repo: 
```
git clone https://github.com/lobanov4real/pgsql-pgadmin-mssql.git
```
2. Go to repo folder: 
```
cd ./pgsql-pgadmin-mssql
```
3. Fill variable values in ``.env`` file. For ``MSDB_TAG`` possible values: ``2022-latest, 2019-latest, 2017-latest``, full tag listing [here](https://hub.docker.com/_/microsoft-mssql-server).
4. Run docker-compose:
```
docker compose up -d
```
5. From host open browser and go to PG Admin console: ``http://<ip_of_docker_server>`` and use values from ``$PG_EMAIL`` and ``$PG_PASSWORD`` for login.
6. In PG Admin console [connect](https://www.pgadmin.org/docs/pgadmin4/development/connecting.html) connect to Postrges SQL server use values from ``DB_USER`` and ``DB_PASSWORD``. The connection can be possible to the server through the value ``password`` in ``DB_PHAM``. More information about ``POSTGRES_HOST_AUTH_METHOD`` [here](https://hub.docker.com/_/postgres).
7. In [MS SSMS](https://learn.microsoft.com/ru-ru/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) connect to MS SQL server use next values: default user is ``SA`` and password from ``MSDB_PASSWORD``.

## License
MIT
