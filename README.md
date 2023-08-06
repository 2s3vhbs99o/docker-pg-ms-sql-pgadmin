# Postgres SQL, PG Admin and MS SQL

I use it for virtual environment when I need run Postgres SQL, PG Admin and MS SQL Express. In my case I use Ubuntu server 20.04 for docker host.
Checked in last (7.3.2) [Redos server](https://redos.red-soft.ru/product/downloads/) with Postgres and PostgresPRO.``

## Prerequisites

1. [Git](https://git-scm.com/downloads)
2. [Docker in Ubuntu 20.04](https://github.com/lobanov4real/installation-guiedes/blob/main/install_docker_ubuntu_20-04.md)

## How to use

1. From terminal clone git-repo:

    ```bash
    git clone https://github.com/lobanov4real/pgsql-pgadmin-mssql.git
    ```

2. Go to repo folder:

    ```bash
    cd ./pgsql-pgadmin-mssql
    ```

3. Fill variable values in **.env** file.

    * For MS SQL:
        * `MSDB_TAG` possible values: `2022-latest, 2019-latest, 2017-latest`, full tag listing [here](https://hub.docker.com/_/microsoft-mssql-server).
        * `MSDB_PASSWORD` is a password for MS SQL sysadmin - SA.
        * `MSSQL_PID` possible values: `Evaluation, Developer, Express, Web, Standard, Enterprise or A product key: #####-#####-#####-#####-#####`.
        * `TZ` a time zone for container, the list of time zones [here](<https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List>).<p>

    ```bash
    vi .env
    ```

4. Run docker-compose:

    ```bash
    docker compose up -d
    ```

5. In browser open **PG Admin** console: ``http://<ip_of_docker_server>`` and use values from ``PG_EMAIL`` and ``PG_PASSWORD`` for login.
6. In PG Admin console [connect](https://www.pgadmin.org/docs/pgadmin4/development/connecting.html) connect to Postrges SQL server use values from ``DB_USER`` and ``DB_PASSWORD``. The connection can be possible to the server through the value ``password`` in ``DB_PHAM``. More information about ``POSTGRES_HOST_AUTH_METHOD`` [here](https://hub.docker.com/_/postgres).
7. In [MS SSMS](https://learn.microsoft.com/ru-ru/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) connect to MS SQL server use next values: default user is ``SA`` and password from ``MSDB_PASSWORD``.

## License

MIT
