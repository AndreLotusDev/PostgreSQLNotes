---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 6:06:46 pm
date modified: sexta-feira, dezembro 13º 2024, 6:10:10 pm
---
Também possuimos operadores de STRING, muito útil para que possamos fazer funções complexas entre duas strings ou mais.

- || = junta duas strings
- CONCAT() = junta duas strings
- LOWER() = transforma uma string toda em LOWERCASE
- LENGTH() = devolve o comprimento de uma frase ou palavra
- UPPER() = transforma tudo para UPPERCASE

Exemplo, iterar a tabela PESSOAS e trazer numa coluna nova chamada nome_completo o primeiro_nome + sobrenome:

```sql
SELECT CONCAT(nome, ' ', sobrenome) AS nome_completo
FROM pessoas;
```
