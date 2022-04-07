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

> 본 예제는 별도 외부(external) 네트워크(net_my) 를 생성 후 기본(default) 네트워크로 지정 후, 2개의 서비스(db, adminer) 컨테이너가 해당 기본 네트워크(default - net_my)를 사용하는 방식을 사용 했다.

- 외부 네트워크를 생성하면 다른 docker-compose 로 생성한 컨테이너와 연결이 용이하기 때문 :)

## 실행

```sh
# 사전작업 : `.sample` 파일을 참조하여 각각의 파일을 만들어 준다.
# 내용 생략

# 외부 네트워크 생성
docker network create net_my

# 외부 네트워크 목록확인
docker network ls

# 도커 컴포즈 실행
docker-compose up -d

# 네트워크 연결 상태 확인
docker network inspect net_my

# adminer 접속
http://localhost:8080
```

## file hierarchy 파일 계층구조

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

## 기타 - 서비스 삭제

> 컨테이너에 올라간 2개 서비스를(db, adminer) 삭제하고자 하는 경우 아래와 같이 입력한다.

- docker-compose.yml 내 service 의 image 추가 또는 버전 변경 등의 작업이 필요한 경우 사용
- data 폴더 백업 등에 주의 ( 개인적으로는 `mv db/data db/old;mkdir db/data` 등과 같은 형태로 처리 추천 )

```sh
docker-compose rm db
docker-compose rm adminer
```

## reference 참조링크

- https://int-i.github.io/sql/2020-12-31/mysql-docker-compose/
- https://hub.docker.com/_/mariadb
- https://docs.docker.com/compose/compose-file/compose-file-v3/
- https://mariadb.com/kb/en/how-to-quickly-insert-data-into-mariadb/
- https://docs.docker.com/compose/
- https://www.daleseo.com/docker-compose-networks/
