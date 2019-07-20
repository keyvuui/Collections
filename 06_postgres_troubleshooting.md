# postgresql troubleshooting guidance

This guidance contains the common problem when using postgres daily.

## Table of content

- [postgresql troubleshooting guidance](#postgresql-troubleshooting-guidance)
  - [Table of content](#Table-of-content)
  - [role "postgres" does not exist](#role-%22postgres%22-does-not-exist)
    - [Description](#Description)
    - [Step](#Step)

## role "postgres" does not exist

### Description

Try to run `createdb -U postgres keyv` but received `createuser: could not connect to database postgres: FATAL:  role "postgres" does not exist`.

It caused by don't have username is postgres. You can force reinitialize database and _force_ use `--username=postgres` specific username.

### Step

1.  Stop the postgres database

    ```shell
    $ brew service stop postgres
    ```

2.  Reinitialize database by force using default username `postgres`.
    ```shell
    $ initdb -E UTF8 --username=postgres -D /usr/local/var/postgres
    ```
3.  Restart postgres database.

    ```shell
    $ brew service start postgres
    ```

4.  Use `psql -U postgres` connect to database, you are good to go.
    ```shell
    $ psql -U postgres
    ```
