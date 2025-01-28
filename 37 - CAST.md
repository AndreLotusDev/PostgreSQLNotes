---
aliases: 
tags: 
date created: Wednesday, January 22nd 2025, 3:56:43 pm
date modified: Wednesday, January 22nd 2025, 3:59:39 pm
---
Podemos utilizar duas formas para fazer CAST de inteiros para numeros flutuantes.

Podemos fazer com o CAST:

```sql
SELECT CAST(int_col as FLOAT) as float_value from numbers;
```

Ou podemos utilizando o operador :: 

```sql
SELECT int_col::FLOAT as float_value
FROM numbers;
```

PS: Isso não se restringe somente aos formatos INT para FLOAT, mas sim de qualquer formato que seja possível migrar de um para o outro, claro que dependendo de qual o formato A para B pode ter perca de dados durante o CAST.