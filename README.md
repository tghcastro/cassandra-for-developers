# Pluralsight [Cassandra for Developers](https://app.pluralsight.com/courses/e4acb31f-9df9-4c15-856b-4700bf6f50a3/table-of-contents)

## CQL (Cassandra Query Language) examples

```CQL
drop keyspace pluralsight;
```

```CQL
create keyspace pluralsight with replication = {'class': 'SimpleStrategy', 'replication_factor': 3};
```

```CQL
create keyspace pluralsight with replication = {'class': 'NetworkTopologyStrategy', 'DC1': 3, 'DC2': 1};
```

```CQL
create table courses (id varchar primary key);
alter table courses add duration int;
alter table courses add released timestamp;
alter table courses add author varchar;
alter table courses with comment = 'A table of courses';
desc table courses;
drop table courses;
```

```CQL
create table couses (
    id varchar primary key,
    name varchar,
    author varchar,
    audience int,
    duration int,
    cc boolean,
    released timestamp
) with comment = 'A table of courses';
```

```CQL
```

## Commands

```shell_script
docker-compose down

docker-compose up -d n1

docker-compose stop n1

docker-compose exec n1 nodetool help

docker-compose exec n1 nodetool status

docker-compose exec n1 nodetool status pluralsight

docker-compose exec n1 nodetool ring

docker-compose exec n1 nodetool ring | grep 679912665146470849

docker-compose exec n1 nodetool describering pluralsight

docker-compose exec n1 more /etc/cassandra/cassandra.yaml

docker-compose exec n1 more /etc/cassandra/cassandra-rackdc.properties

docker-compose exec n1 cqlsh
```
