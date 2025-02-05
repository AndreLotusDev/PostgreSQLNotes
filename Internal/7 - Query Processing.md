---
aliases: 
tags: 
date created: Tuesday, February 4th 2025, 9:45:45 pm
date modified: Tuesday, February 4th 2025, 10:07:45 pm
---
Quando o PostgreSQL recebe uma query, ele quebra em etapas, tais quais são:

- Parser
	- O parser é responsável por avaliar se a query que você escreveu de fato é uma query válida. E se não entregar uma mensagem de erro dizendo exatamente onde você falhou na escrita da query. Após isso é produzido o que chamamos de query Tree.
- Rewrite
	- Ele faz o processo de decompor a query e verificar se a query pode ser feita de uma forma mais eficiente. Geralmente muito usado no processo de construção de views, mas também pode ser aplicado no processo de construção de queries.
- Planner
	- Baseado no que você precisa e como você construiu essa query, o planner irá analisar a melhor forma de isso ser feito/excecutado. Exemplo: ao analisar com o planner uma query ele pode optar usar o INDEX ou dar fetch diretamente numa tabela.
- Executer
	- Executa de fato a query.

---

# Explain vs Explain Analyse

Quando você executa um `EXPLAIN` você está pedindo para o PostgreSQL te dar um plano de execução da query, ou seja, como ele irá executar a query. 

Quando você executa um `EXPLAIN ANALYSE` você está pedindo para o PostgreSQL te dar um plano de execução da query, e também executar a query e te entregar o tempo que a query levou para ser executada.

PS: Dentro do pgAdmin ele fornece uma ferramenta built in que fornece não somente as informações do EXPLAIN e EXPLAIN ANALYSE como também fornecesse uma visão gráfica do processo.

![[Pasted image 20250204220036.png]]