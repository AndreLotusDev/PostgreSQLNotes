---
aliases: 
tags: 
date created: Sunday, February 9th 2025, 3:26:44 pm
date modified: Sunday, February 9th 2025, 3:59:12 pm
---
Assim como o CTE tem o que chamamos Recursive Common Table Expression, também para a VIEW temos a VIEW materializada. Ou seja, a VIEW e o CTE são ferramentas de conveniencia que te ajudam a construir QUERIES, enquanto Recursive Common Table Expression e View Materializada adicionam maior funcionalidade ao dois items.

Um bom exemplo para se ter uma view materializada seriam ranks semanais dentro de uma rede social, como a view materializada precisa ser reatualizada toda hora para ter os dados mais quentes (hot), então situações que mudam pouco ou tem um controle de contexto bem definido são mais elegantes para se utilizar views materializadas.

---

Para criar uma view materializada:

```sql
CREATE MATERIALIZED VIEW mv_categorias_mais_vendidas AS
SELECT 
    c.id AS categoria_id,
    c.nome AS categoria,
    SUM(v.quantidade) AS total_vendido
FROM categorias c
JOIN produtos p ON c.id = p.categoria_id
JOIN vendas v ON p.id = v.produto_id
GROUP BY c.id, c.nome
ORDER BY total_vendido DESC;
```

Para atualizar uma view materializada (com dados):

```sql
REFRESH MATERIALIZED VIEW mv_categorias_mais_vendidas;
```

Você pode também permitir leituras sujas sem bloquear tais leituras adicionar a KEYWORD CONCURRENTLY:

```sql
REFRESH MATERIALIZED VIEW CONCURRENTLY mv_categorias_mais_vendidas;
```
