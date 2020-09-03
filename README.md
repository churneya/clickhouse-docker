# clickhouse with docker-compose running

## How to run

```code
docker-compose up -d server
```

## access address

```code
http interface http://127.0.0.1:8123
for native client connect port 9000
for mysql client connect port 9004
```

## how to Connect server

```code
with docker client

docker run -it yandex/clickhouse-client --host ${serverip|hostip}
```

## import data

* create table

```code

CREATE TABLE wikistat
(
    project String,
    subproject String,
    hits UInt64,
    size UInt64
) ENGINE = Log;

```

* insert  data

```code
docker run -i yandex/clickhouse-client  --format_csv_delimiter="|" --host ${serverhost} --query="INSERT INTO d
efault.wikistat3 FORMAT CSV" < ./data/info.csv
```

* select result

> use ui tools HouseOps https://github.com/HouseOps/HouseOps

```code
select * from default.wikistat;
```
