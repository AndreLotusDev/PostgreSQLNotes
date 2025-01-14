---
aliases: 
tags: 
date created: Wednesday, January 1st 2025, 6:54:52 am
date modified: Tuesday, January 7th 2025, 7:40:14 am
---
- A ordem entre 'FROM' e 'JOIN' frequentemente faz muita diferença
- Nós vemos dar contexto se o nome das colunas colidirem, exemplo, duas colunas ID proveniente de duas tabelas diferentes...
- Tabelas podem ser renomeadas usando a KEYWORD 'AS'
- Ha multiplas possibilidades de JOIN

---

INNER JOIN: Só ocorre quando os dois lados do JOIN, então o select produzido entre as duas tabelas não irá trazer um lado NULL e o outro preenchido em certas situações. (todas as colunas de uma linha referente a tabela B como nulo).

LEFT OUTER JOIN: Quando você quer que retorne todos os elementos da tabela a esquerda mesmo que isso signifique performar o JOIN  e trazer coisas nulas do lado DIREITO.

RIGHT OUTER JOIN: Mesma que a de cima, todavia só que do lado direito.

FULL JOIN: Não importa se tem correspondencia entre o lado A e B, se tive uma linha em B traga mesmo que o lado A ficara nulo e vice versa.

### Resumo:

- **INNER JOIN**: Apenas registros com correspondência em ambas as tabelas.
    
- **LEFT JOIN**: Todos os registros da tabela à esquerda e correspondências da tabela à direita.
    
- **RIGHT JOIN**: Todos os registros da tabela à direita e correspondências da tabela à esquerda.
    
- **FULL JOIN**: Todos os registros de ambas as tabelas, com ou sem correspondência.

---
