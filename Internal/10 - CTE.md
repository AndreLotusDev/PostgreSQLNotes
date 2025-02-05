---
aliases: 
tags: 
date created: Tuesday, February 4th 2025, 11:17:43 pm
date modified: Tuesday, February 4th 2025, 11:24:15 pm
---
CTE ou common table expression é um sintaxe que permite escrever tabelas para serem executadas nas queries, permitindo que aumento a legibilidade das queries.

Basicamente eu posso construir subqueries ao qual eu posso usar a posteriori.

Exemplo:

```sql
WITH tags AS(
	SELECT user_id, created_at FROM caption_tags
	UNION ALL
	SELECT user_id, created_at FROM photo_tags
)
SELECT username, tags.created_at
FROM users
JOIN tags ON tags.user_id = user.id
WHERE tags.created_at < '2010-01-07';
```