# Postgres SQL, PG Admin and MS SQL

I use it for virtual environment when I need run Postgres SQL, PG Admin and MS SQL Express. In my case I use Ubuntu server 20.04 for docker host.
Checked in last (7.3.2) [Redos server](https://redos.red-soft.ru/product/downloads/) with Postgres and PostgresPRO.

## Prerequisites

- [Git](https://git-scm.com/downloads)
- [Docker](https://docs.docker.com/get-docker/)

## How to use

**Clone git-repo**

```shell
git clone https://github.com/2s3vhbs99o/docker-pg-ms-sql-pgadmin.git
```

**Go to repo folder**

```shell
cd ./pgsql-pgadmin-mssql
```

**Fill variable values in **.env** file**

```shell
vim .env
```

   * For Postgres:
        * `DB_TAG` is `latest`. Possible values [here](https://hub.docker.com/_/postgres).
        * `DB_USER` provide a superuser
        * `DB_PASSWORD` is a password for superuser
        * `DB_PHAM` is `POSTGRES_HOST_AUTH_METHOD`. More information about it [here](https://hub.docker.com/_/postgres).
   * For PG Admin:
        * `PG_TAG` is `latest`. Possible values [here](https://www.pgadmin.org/docs/pgadmin4/latest/container_deployment.html)
        * `PG_EMAIL` provide a login email.
        * `PG_PASSWORD` provide a password for login.
   * For MS SQL:
        * `MSDB_TAG` possible values: `2022-latest, 2019-latest, 2017-latest`, full tag listing [here](https://hub.docker.com/_/microsoft-mssql-server).
        * `MSDB_PASSWORD` is a password for MS SQL sysadmin - `SA`.
        * `MSSQL_PID` possible values: `Evaluation, Developer, Express, Web, Standard, Enterprise or A product key: #####-#####-#####-#####-#####`.
        * `TZ` a time zone for container, the list of time zones [here](<https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List>).

**Run docker-compose**

```shell
docker compose up -d
```

**Open PG Admin console**

- In browser open **PG Admin** console: [http://<ip_of_docker_server>](https://github.com/lobanov4real/pgsql-pgadmin-mssql/blob/master/README.md#how-to-use) and use values from `$PG_EMAIL` and `$PG_PASSWORD` for login.

- In **PG Admin** console [connect](https://www.pgadmin.org/docs/pgadmin4/development/connecting.html) to Postrges SQL server use default db `postgres` and values from `$DB_USER` and `$DB_PASSWORD`. The connection can be possible to the server through the value ``password`` in `$DB_PHAM`.

- In [MS SSMS](https://learn.microsoft.com/ru-ru/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) connect to MS SQL server use default user `SA` and password from value `$SA_PASSWORD`.

## License

MIT
