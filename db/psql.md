# PostgreSQL
* Entering PSQL shell
    ```bash
    # Use the operating system user 'postgres' 
    $ sudo -u postgres -i
    # Then enter psql
    $ psql
    ```
* Getting list of databases
    ```psql
    postgres=# \l
    ```
* Switching database
    ```psql
    postgres=# \c {dbname}
    ```
    For example:
    ```psql
    postgres=# \c book
    ```
* Getting list of tables
     ```psql
    book=# \dt
    ```
* Export database
    ```psql
    pg_dump -U {username} -h {hhostname} {dbname} > {exportfile}.pqsql
    ```
    For example:
    ```psql
    pg_dump -U mocatfrio -h localhost book > book_dump.pgsql
    ```
    Then, system will ask the password.

* Create database
    Before importing a database, you must create it first in your local.
    ```psql
    postgres-# CREATE DATABASE book;
    CREATE DATABASE
    ```
* Getting list of roles
    ```psql
    postgres=# \du
    ```
* Create new roles
  * CREATE USER is the same as CREATE ROLE except that it implies LOGIN
  * Create a role that can override all access restrictions within the database (superuser), create databases, and create roles:
    ```psql
    CREATE USER username WITH PASSWORD 'password' SUPERUSER CREATEDB CREATEROLE;
    ```
    For example:
    ```psql
    CREATE USER mocatfrio WITH PASSWORD 'kucinglucu' SUPERUSER CREATEDB CREATEROLE;
    ```
* Import database
    ```bash
    psql -U {username} {dbname} < {exportfile}.pgsql
    ```
    For example:
    ```bash
    psql -U postgres book < book_dump.pgsql
    ```

