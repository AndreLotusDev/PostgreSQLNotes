---
aliases: 
tags: 
date created: quarta-feira, dezembro 18º 2024, 11:10:21 am
date modified: quarta-feira, dezembro 18º 2024, 11:20:21 am
---
ID's gerados automaticamente geralmente são identificadores únicos geralmente sendo GUIDS, sorted GUIDS, ou números.

Onde cada item novo adicionado na tabela ela automaticamente sabe qual será o próximo número.

Para fazer isso automaticamente dentro do postgreSQL podemos fazer da seguinte maneira:

```sql
CREATE TABLE users(
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);
```

O SERIAL keyword é um tipo de dado que é auto incrementado, e o PRIMARY KEY é uma restrição que garante que o id será único. Além do mais que garante performance adicional ao procurar pelo ID dentro da tabela.
