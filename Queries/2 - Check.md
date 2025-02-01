---
aliases: 
tags: 
date created: Friday, January 24th 2025, 11:36:55 am
date modified: Monday, January 27th 2025, 9:37:18 pm
---
```sql
create table products (
id serial primary key,
name varchar(100),
sector varchar(200)
)

alter table products
add column price integer;

alter table products
add check (price > 0);

insert into products (name, sector, price)
values ('T-shirt', 'cloth', 0);
```

```sql
create table cars (
id serial primary key,
color varchar(20) check (color in ('red', 'blue', 'green')),
name varchar(100)
);

insert into cars (name, color) values ('mustang', 'yellow');
```