---
aliases: 
tags: 
date created: Wednesday, January 22nd 2025, 2:39:21 pm
date modified: Wednesday, January 22nd 2025, 3:13:21 pm
---
Essa função já vem de forma nativa no Postgres SQL, ela itera uma coluna multi valorada e encontra o maior valor, diferente do MAX ela não itera ROW por ROW, ela itera dentro da coluna um array tentando encontrar o maior valor.

Por exemplo, podemos usar o GREATES para achar a ultima data:

```sql
SELECT 
    OrderID,
    GREATEST(
        COALESCE(CreatedDate, '1970-01-01'),
        COALESCE(ShippedDate, '1970-01-01'),
        COALESCE(DeliveredDate, '1970-01-01')
    ) AS LatestActivityDate
FROM 
    ORDERS;
```