---
aliases: 
tags: 
date created: Tuesday, February 4th 2025, 10:07:45 pm
date modified: Tuesday, February 4th 2025, 10:53:09 pm
---
É possível no postgreSQL ter estatisticas coletável que pode ser buscada a posteriori para analise de query. Para fazer isso basta executar o seguinte comando.

SELECT *
FROM pg_stats
WHERE tablename = 'users';

Essa query vai trazer informações cruciais de status e estatistica sobre a tabela.

Com o retorno dessa tabela, é com isso que o query planner ve qual será o melhor caminho deverá seguir.

![[Pasted image 20250204221553.png]]