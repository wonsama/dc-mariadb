# dc-mariadb

> docker compose for maria db

mariadb 와 손쉽게 db 확인을 위한 adminer 를 설치하는 방법을 공유한다.
( 필요에 따라 adminer 는 주석 처리 하여 미 사용하는 것도 권장한다 )

## must todo 반드시 해야 될 것

> `.sample` 파일을 참조하여 `.sample` 확장자가 지워진 파일을 만들어야 된다.

(필수)

```sh
# docker-compose 설정
docker-compose.yml.sample
# DB 연결 암호 등 설정
.env
# DB 캐릭터셋 등 설정
./db/conf.d/my.cnf
```

(옵션)

```sh
# 최초 테이블 생성
./db/initdb.d/create_table.sql
# 최초 데이터 적재
./db/initdb.d/load_data.sql
```

## network 생성

> 본 예제는 별도 네트워크

> 필요에 따라 별도 network 를 만들어 추후 연결해도 좋을 것 같음
> external network 를 만드는 경우 container 를 내려도 지워지지 않음에 유의

```sh
# sample
docker network create net_app
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
