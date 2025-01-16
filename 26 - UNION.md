---
aliases: 
tags: 
date created: Wednesday, January 15th 2025, 9:10:18 pm
date modified: Wednesday, January 15th 2025, 9:23:07 pm
---
A KEYWORD Union geralmente é utilizada para se unir duas tabelas que são identicas, todavia com filtros e propositos diferente.

Lembrando que podemos usar UNION ALL, ao qual se uma ROW for repetida ele mostra mesmo assim.
	O Union All por não produzir verificação acaba que por fim pode ser mais rápido.

Exemplo:

```SQL
(select o.product_name, o.price * o.quantity_sold as total, 'Least sold' as tag
from orders o 
order by o.price * o.quantity_sold
offset 2
limit 2)
UNION
(select o.product_name, o.price * o.quantity_sold as total, 'Most sold' as tag
from orders o 
order by o.price * o.quantity_sold desc
offset 2
limit 2) order by total desc;
```

---

PS: O Union para ser usado as duas tabelas devem ter as mesmas colunas, e essas mesmas colunas devem ter seus type values identicos, ou seja, se duas tabelas tem as mesmas colunas, mas numa tabela A coluna A tem formato STRING, e na tabela B coluna A tem formato INTEGER então será produzido um erro ao final.