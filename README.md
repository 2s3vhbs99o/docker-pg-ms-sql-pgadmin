# Postgres SQL, PG Admin and MS SQL

I use it for virtual environment when I need run Postgres SQL, PG Admin and MS SQL Express. In my case I use Ubuntu server 20.04 for docker host.
Checked in last (7.3.2) [Redos server](https://redos.red-soft.ru/product/downloads/) with Postgres and PostgresPRO.

## Prerequisites

1. [Git](https://git-scm.com/downloads)
2. [Docker in Ubuntu 20.04](https://github.com/lobanov4real/installation-guiedes/blob/main/install_docker_ubuntu_20-04.md)

## How to use

1. From terminal clone git-repo:

    ```shell
    git clone https://github.com/lobanov4real/pgsql-pgadmin-mssql.git
    ```

2. Go to repo folder:

    ```shell
    cd ./pgsql-pgadmin-mssql
    ```

3. Fill variable values in **.env** file.

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

4. Issue certificate for MS SQL docker container and convert `.pem` to `.crt` for ca-certificates:

    ```shell
    sudo openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql' -keyout  ./files/mssql.key -out  ./files/mssql.pem -days 365
    ```

    ```shell
    sudo openssl x509 -outform der -in ./files/mssql.pem -out ./files/mssql.crt
    ```

5. Create mssql.conf file:

    ```shell
    sudo vi ~/mssqlvol/mssql.conf
    ```

    ```editorconfig
    [network]
    tlscert = /etc/ssl/certs/mssql.pem
    tlskey = /etc/ssl/private/mssql.key
    tlsprotocols = 1.2
    forceencryption = 1
    ```

6. Run docker-compose:

    ```shell
    docker compose up -d
    ```

7. In browser open **PG Admin** console: [http://<ip_of_docker_server>](https://github.com/lobanov4real/pgsql-pgadmin-mssql/blob/master/README.md#how-to-use) and use values from `$PG_EMAIL` and `$PG_PASSWORD` for login.

8. In **PG Admin** console [connect](https://www.pgadmin.org/docs/pgadmin4/development/connecting.html) to Postrges SQL server use default db `postgres` and values from `$DB_USER` and `$DB_PASSWORD`. The connection can be possible to the server through the value ``password`` in `$DB_PHAM`.

9. In [MS SSMS](https://learn.microsoft.com/ru-ru/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) connect to MS SQL server use default user `SA` and password from value `$SA_PASSWORD`.

## License

MIT
