# dc-mariadb

docker compose maria db

## hierarchy 계층구조

```txt
- db
  - conf.d
    - my.cnf
  - data
    - ...
  - initdb.d
    - create_table.sql
    - load_data.sql
- docker-compose.yml
- .env
```

## reference 참조링크

- https://int-i.github.io/sql/2020-12-31/mysql-docker-compose/
- https://hub.docker.com/_/mariadb
- https://docs.docker.com/compose/compose-file/compose-file-v3/
- https://mariadb.com/kb/en/how-to-quickly-insert-data-into-mariadb/
