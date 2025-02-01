---
aliases: 
tags: 
date created: Thursday, January 30th 2025, 8:56:41 am
date modified: Thursday, January 30th 2025, 9:01:12 am
---
Podemos performar as queries do dia a dia normalmente que a IDE vai nos retornar quanto tempo foi levado para se performar uma query, todavia também é possível analisar uma QUERY de outra forma. Usando por exemplo a keyword EXPLAIN ANALYSE.

Exemplo:

```sql
EXPLAIN ANALYSE SELECT * FROM users
WHERE username = 'Emil30';
```

E em vez de retornar os resultados da QUERY, ele vai retornar uma QUERY PLAN, ou seja, quanto tempo demorou para executar e planejar.

Exemplo:

```plaintext
QUERY PLAN
---------------------------------------------------------------------------------------------------------------------------
Index Scan using idx_username on users  (cost=0.29..8.30 rows=1 width=45) (actual time=0.023..0.024 rows=1 loops=1)
  Index Cond: (username = 'Emil30'::text)
  
Planning Time: 0.075 ms
Execution Time: 0.042 ms
```