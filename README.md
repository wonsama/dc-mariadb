# dc-mariadb

docker compose maria db

## must todo 반드시 해야 될 것

> `.sample` 파일을 참조하여 `.sample` 확장자가 지워진 파일을 만들어야 된다.

(필수)

```txt
.env
./db/conf.d/my.cnf
```

(옵션)

```txt
./db/initdb.d/create_table.sql
./db/initdb.d/load_data.sql
```

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
- https://docs.docker.com/compose/
- https://www.daleseo.com/docker-compose-networks/
