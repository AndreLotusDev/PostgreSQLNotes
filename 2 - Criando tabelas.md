---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 4:13:30 pm
date modified: sexta-feira, dezembro 13º 2024, 4:19:41 pm
---
Podemos rodar um banco online para fazer pequenos testes.
Para isso basta acessar pg-sql.com.

---

## Criando a primeira tabela do tipo cities

```sql
CREATE TABLE cities (
	name VARCHAR(50),
	country VARCHAR(50),
	population INTEGER,
	area INTEGER
);
```

Se você for analisar de forma purista, a tabela cities tem uma coluna chamada country, que de certa forma pode ser utilizada como um VARCHAR, mas se quisermos realmente seguir todos os padrões SQL devemos tornar isso uma tabela onde podemos apontar usando uma FK.

Ao utilizar assim sem padronização e apontando para outra tabela e portanto contendo repetição estamos utilizando o padrão NO SQL.