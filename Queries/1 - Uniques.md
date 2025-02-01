---
aliases: 
tags: 
date created: Friday, January 24th 2025, 11:29:30 am
date modified: Friday, January 24th 2025, 11:29:34 am
---
```sql
create table products (

id serial primary key,

name varchar(100),

sector varchar(200)

)

  

insert into products (name, sector)

values ('T-shirt', 'cloth');

  

alter table products add unique (name);

  

SELECT conname

FROM pg_constraint

WHERE conrelid = 'products'::regclass AND contype = 'u';

alter table products drop constraint products_name_key;

  

alter table products add unique (name, sector);

  

insert into products (name, sector)

values ('T-shirt', 'cloth');

  

select * from products;
```