---
aliases: 
tags: 
date created: Wednesday, January 22nd 2025, 3:15:58 pm
date modified: Wednesday, January 22nd 2025, 3:20:04 pm
---
O operador CASE do POSTGRESQL é muito útil quando queremos criar cenários assim como nas linguagens de programação de IF, por exemplo, precisamos iterar a tabela de produto, SE o preço for 100 imprima o valor 'BAIXO', SE o preço for 200 imprima o valor 'ALTO' e assim vai.

Exemplo:

```sql
SELECT 
    ProductID,
    ProductName,
    Price,
    CASE
        WHEN Price > 100 THEN 'HIGH'
        WHEN Price BETWEEN 50 AND 100 THEN 'MEDIUM'
        ELSE 'LOW'
    END AS PriceCategory
FROM 
    Product;
```