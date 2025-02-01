---
aliases: 
tags: 
date created: Thursday, January 30th 2025, 9:14:05 am
date modified: Thursday, January 30th 2025, 9:16:49 am
---
Geralmente quando criamos um index, por default o postgresql cria um do tipo b tree, todavia podemos escolher outros tipos de indexes para anexar a nossa tabela.

Tipos de index:
- B-Tree (na maior parte do tempo precisaremos somente desse aqui).
- Hash - Usado para comparação de valores.
- GiST - Busca geometrica ou de full text search.
- SP-GiST - Dados elencados, como datas, por exemplo muitas linhas podem ter o mesmo ano.
- GIN - Para colunas multivaloradas ou com JSON.
- BRIN - Especializado para largos datasets.