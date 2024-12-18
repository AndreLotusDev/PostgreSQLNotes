---
aliases: 
tags: 
date created: quarta-feira, dezembro 18º 2024, 11:40:08 am
date modified: quarta-feira, dezembro 18º 2024, 11:50:06 am
---
Devemos não somente configurar unique identifier e foreign keys, mas ao mesmo tempo garantir que esses dados estejam consistentes ao longo do tempo. Portanto muitas pessoas acabam delegando essa tarefa de deixar tudo consistente do lado da API, o que acaba por fim causando bottlenecks, sempre que possivel configure constraints do lado do banco, garantindo assim que sempre os dados inseridos ou atualizados dentro do banco de dados estejam consistentes.

Assim como não deve ser possivel não inserir uma PESSOA que não existe dentro da tabela TRABALHADOR, o mesmo é valido pro flow de atualizar, assim como não deve ser possível adicionar dentro da tabela TRABALHDOR na coluna PESSOA_ID um ID null. Portanto é devido isso a importância de constraints. 

O mesmo para fluxos de deleção.