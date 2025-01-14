---
aliases: 
tags: 
date created: Tuesday, January 14th 2025, 7:37:42 pm
date modified: Tuesday, January 14th 2025, 8:35:47 pm
---
Temos dois tipos de agregação: grouping, aggregates.

---

Grouping by: 
- Reduz várias rows em poucas rows.
- Feito usando a clausula GROUP BY.
- Visualizar o resultado como um agrupamento de KEYS é crucial enquanto usando essa KEYWORD.

Dentro do group by podemos usar a clausula HAVING, muito útil para poder filtrar conteudo.

Como é feito o processo: 
	Exemplo: Existe uma tabela compras, e nela tem o usuario id, podemos agrupar a tabela compras por PRODUTO_ID, e assim podemos descobrir qual produto foi mais comprado dentro dessa tabela...
	Quando executamos o processo de group by é feito um ajuntamento e agrupamento row por row e organizado por PRODUTO_ID.
	![[Pasted image 20250114194732.png]]
	![[Pasted image 20250114194918.png]]

---

Aggregates:
- Reduz muitos valores para apenas um.
- Feito usando funções de agregação.

Tipos de operadores de agregação: COUNT(), SUM(), AVG(), MIN(), MAX().

PS: Não é possível fazer uma operação de agregação ao mesmo tempo que eu faço uma operação de seleção normal, exemplo:

SELECT SUM(id), id
FROM comments;

---

Como você pode observar, geralmente operadores de GROUP BY e AGREGACAO geralmente podem ser utilizados em conjunto e fazem muito sentido serem utilizados em conjunto.