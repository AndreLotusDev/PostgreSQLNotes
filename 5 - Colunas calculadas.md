---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 5:54:57 pm
date modified: sexta-feira, dezembro 13º 2024, 6:02:19 pm
---
SQL não necessariamente significa somente estacionar dados em uma tabela, mas significa também processos complexos, podemos misturar colunas, somar colunas, usar uma coluna para definir de onde trazer o dado de outra coluna e entre outras operações full turing que a programação nos permite fazer.

Esses são os operadores que o PostgreSQL permite utilizar para calcular colunas:

**Operadores Aritméticos**

Usados para realizar cálculos matemáticos básicos.

|Operador|Descrição|Símbolo|
|---|---|---|
|Adição|Soma de dois valores|`+`|
|Subtração|Subtração de dois valores|`-`|
|Multiplicação|Multiplica dois valores|`*`|
|Divisão|Divide dois valores|`/`|
|Módulo|Resto da divisão inteira|`%`|
|Exponenciação|Potência de um valor|`^`|

Podemos também utilizar o @ para valores absolutos e |/ para raiz quadrada no PostreSQL.

Por exemplo, vamos supor que temos uma TABELA cidades, e nela temos as colunas população e area, e queremos calcular a densidade populacional, podemos fazer da seguinte forma:

```sql
SELECT nome, população, area, população/area as densidade_populacional
FROM cidades;
```

