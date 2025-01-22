---
aliases: 
tags: 
date created: Wednesday, January 22nd 2025, 10:12:07 am
date modified: Wednesday, January 22nd 2025, 10:20:57 am
---
O operador DISTINC permite que selecionamos resultados únicos de uma TABLE RESULT, evitando assim duplicação, por exemplo podemos pegar dentro de uma tabela de clientes todos os países que foi efetuado a compra sem que traga duplicatas.

Exemplo:

```sql
SELECT DISTINCT Country
FROM CUSTOMERS;
```

Outro exemplo, eu preciso saber dentro da tabela PRODUTOS quantos tipos diferentes de departamentos eu tenho.

```sql
SELECT COUNT(DISTINCT department)
FROM products;
```