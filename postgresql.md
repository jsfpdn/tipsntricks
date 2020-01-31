# PostgreSQL

When updating between major version (e.g. 11.x to 12.x), PostgreSQL server may not start:

```bash
> psql postgres

psql: error: could not connect to server: could not connect to server: No such file or directory
    Is the server running locally and accepting
    connections on Unix domain socket "/tmp/.s.PGSQL.5432"?

> postgres -D /usr/local/var/postgres

2020-01-31 12:23:37.745 CET [36474] FATAL:  database files are incompatible with server
2020-01-31 12:23:37.745 CET [36474] DETAIL:  The data directory was initialized by PostgreSQL version 11, which is not compatible with this version 12.1.
```

To fix this, run

```bash
> brew postgresql-upgrade-database
```
