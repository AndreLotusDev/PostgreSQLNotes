---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 5:49:31 pm
date modified: sexta-feira, dezembro 13º 2024, 5:51:09 pm
---
Após criar uma tabela, configurar essa tabela e suas colunas e por fim inserir dados nessa coluna, podemos dar retrieve dessa informação usando a clausula SELECT, podemos trazer toda a informação da tabela da seguinte forma:

```sql
SELECT * FROM nome_da_tabela;
```

Podemos configurar e selecionar somente algumas colunas da tabela todavia trazendo todas as LINHAS da TABELA:

```sql
SELECT nome_da_coluna1, nome_da_coluna2 FROM nome_da_tabela;
```

Ou podemos além de filtrar por culunas, tambem podemos ordenar e trazer somente os 10 últimos INSERTS:

```sql
SELECT nome_da_coluna1, nome_da_coluna2 FROM nome_da_tabela ORDER BY nome_da_coluna1 DESC LIMIT 10;
```
