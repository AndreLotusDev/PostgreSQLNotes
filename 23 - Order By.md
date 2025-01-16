---
aliases: 
tags: 
date created: Wednesday, January 15th 2025, 8:52:06 pm
date modified: Wednesday, January 15th 2025, 8:55:21 pm
---
A clausula ORDER BY é bem simples, basicamente fala ao SQL como a tabela final irá ser apresentada ao usuário final.

Caso seja executado um ORDER BY u.primeiro_nome ASC, então a tabela irá vir ordenada alfabeticamente pelo primeiro nome.

Caso contrário, se feito com um ORDER BY u.primeiro_nome DESC, então a tabela irá vir ordenada descendentemente.

--- 

Podemos também ordernar por mais de uma coluna, como por exemplo:

ORDER BY u.primeiro_nome, u.ultimo_nome.

Com isso eu ordeno alfabeticamente pelo primeiro nome e depois pelo último nome. 