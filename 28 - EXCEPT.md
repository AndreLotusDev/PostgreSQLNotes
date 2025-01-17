---
aliases: 
tags: 
date created: Thursday, January 16th 2025, 10:14:19 am
date modified: Thursday, January 16th 2025, 10:20:21 am
---
A KEYWORD EXCEPT funciona de forma oposta a INTERSECT, enquanto a INTERSECT opera trazendo o que tem em comum entre dois dataset,o EXCEPT executa uma analise e somente traz o que de um não tem no outro.

---

Um cenário ideal para o uso de EXCEPT por exemplo pode ser o sync ou analise de diferenca entre duas tabelas.

Vamos supor que voce tem uma tabela de backup.

Voce tem ORDERS and BACKUP_ORDERS, com o EXCEPT voce pode executar uma QUERY ao qual vai saber quais items ainda não estão na tabela BACKUP_ORDER e finalmente inserir para que estejam em perfeita sincronia.

```sql
SELECT customer_id 
FROM customers_main
EXCEPT
SELECT customer_id 
FROM customers_backup;
```