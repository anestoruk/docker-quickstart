Docker some useful containers quickstart

## Content
- [Postgres DB](#postgres-db)
- [Oracle DB XE](#oracle-db-xe)
- [Kafka with Kafdrop](#kafka-with-kafdrop)

## Postgres DB

run docker container:
```
docker run --name postgres-db -d -p 5432:5432 \
	-e POSTGRES_PASSWORD=postgres \
	postgres
```

connect to database: `localhost:5432/postgres` with username: `postgres` and password: `postgres`

```
CREATE DATABASE mydatabase;
CREATE USER myuser WITH ENCRYPTED PASSWORD 'myuser';
GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;
```

## Oracle DB XE

get oracle images from git:
```
git clone https://github.com/oracle/docker-images.git
cd docker-images/OracleDatabase/SingleInstance/dockerfiles
```

build image:
```
./buildContainerImage.sh -v 18.4.0 -x
```

run docker container:
```
docker run --name oracle-db -d -p 1521:1521 -p 5500:5500 \
	-e ORACLE_PWD=system \
	-e ORACLE_CHARACTERSET=AL32UTF8 \
	-d oracle/database:18.4.0-xe
```

connect to database: `localhost:1521/XEPDB1` with username: `system` and password: `system`

```
CREATE USER myuser IDENTIFIED BY myuser;
GRANT ALL PRIVILEGES TO myuser;
```


## Kafka with Kafdrop
```
docker-compose -f kafka/docker-compose.yml up -d
```
