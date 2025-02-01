---
aliases: 
tags: 
date created: Tuesday, January 28th 2025, 10:42:48 am
date modified: Thursday, January 30th 2025, 9:21:22 am
---
Para evitarmos procurar um por um no HD em busca de um item no banco de dados, criamos indices, claro que com pequenos volume de dados essa diferença não é notada, todavia a criação de diversos tipos de indices beneficiam a leitura de dados e infelizmente atrasam a inserção de dados, claro que com o trade off correto podemos fazer o trade off mais adequado para cada tipo de situação.

PS: Ou seja, criar um INDEX é contar para o POSTGRESQL para dependendo o tipo de QUERY executar de uma forma diferente por debaixo dos panos caso exista uma INDEX que possa ser usado na QUERY.

![[Pasted image 20250128104514.png]]

PS: Ou seja, sempre devemos evitar full table scan em tabelas com grandes volumes de dados.

Quando fazemos full table scan o PG tem que carregar todas as rows que estão no arquivo HEAP para a memoria. (ou seja, geralmente induz a baixa performance).

![[Pasted image 20250128105600.png]]

![[Pasted image 20250128105659.png]]

O index é como se fosse um livro de ordenação onde aponta exatamente ou aproximadamente onde nosso dado (row e colunas) estará dentro do HEAP em um bloco mais especifico.

---

## Processo de indexação

1 - Setamos o index em username

![[Pasted image 20250128105932.png]]

2 - Logo teremos um livro de gravações ordenados, falando onde tal chave está localizada dentro do HEAP, por bloco e index.

![[Pasted image 20250128110046.png]]
![[Pasted image 20250128111419.png]]
![[Pasted image 20250128111539.png]]![[Pasted image 20250128111920.png]]
Link sobre como as estruturas b tree são organizadas e são a base do banco de dados: https://www.youtube.com/watch?v=K1a2Bk8NrYQ

---

Notas: Não necessariamente um index pode aumentar a performance de todas as suas QUERIES, por exemplo, alguns indexes podem ser criados mas nunca serem usados, isso pode acontecer. Por isso é importante analisar as QUERIES dentro de seu sistema e somente criar INDEXES que realmente façam sentido.

- Postgresql cria automaticamente indexes para colunas do tipo chave primária.
- Postgresql automaticamente cria indexs para qualquer coluna do tipo UNIQUER.
- Esses index geralmente não são listados debaixo de indexes por exemplo no PGAdmin UI.

Você pode verificar todos esses indexes com a seguinte query:

```sql
SELECT relname, relkind
FROM pg_class
WHERE relkind = 'i';
```

---

## Como criar indexs

CREATE INDEX ON users (username);
	PS: Por debaixo dos panos o postgresql irá criar um index chamado: user_username_idx

## Como dropar um index

DROP INDEX user_username_idx;

---