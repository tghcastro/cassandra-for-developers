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
alter table courses with comment = 'A table of courses';
desc table courses;
drop table courses;
```

```CQL
create table courses (
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
desc pluralsight;
desc tables;
desc table courses;
```

```CQL
expand on;
select * from courses;
expand off;
```

```CQL
tracing on;
select * from courses;
tracing off;
```

```CQL
select id, cc, writetime(cc) from courses where id = 'advanced-javascript';
update courses set cc = false where id = 'advanced-javascript';
select id, cc, writetime(cc) from courses where id = 'advanced-javascript';
```

```CQL
select id, token(author), token(cc) from courses;
```

```CQL
update users using ttl 120 set reset_token = 'abc123' where id = 'john-doe';
select ttl(reset_token) from users where id = 'john-doe';
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
