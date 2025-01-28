---
aliases: 
tags: 
date created: Wednesday, January 22nd 2025, 3:48:14 pm
date modified: Wednesday, January 22nd 2025, 4:24:58 pm
---
Temos vários tipos de formatos para data types, alguns que são possíveis dentro do PostgreSQL, lembrando que, nem todos os formatos de um SQL é compatível com outro tipo de banco, cada tipo de banco tem seus tipos suportados.

- Numbers
	- smallint
	- integer
	- bigint
	- smallserial
	- serial
	- bigserial
	- decimal
	- numeric
	- real
	- double precision
	- float
- Currency
- Binary
- Interval
	- 1 day -> 1 day
	- 1D -> 1 day
	- 1D 1M 1S  -> 1 day 1 minute 1 second
- Date/Time
	- 1980-11-20
	- Nov-20-1980
	- 20-Nov-1980
	- 1980-November-20
	- November 20, 1980
	- 01:23 AM -> 01:23, no time zone
	- 05:23 PM -> 17:23, no time zone
	- 20:34 -> 20:34, no time zone
	- 01:23 AM EST 01:23-05:00
	- 05:23 PM PST 17:@3-08:00
	- 05:23 PM UTC 17:23+00:00
	- 05:23 PM UTC 17:23+00:00
	- Nov-20-1980 05:23 PM PST -> 1980-11-20 18:23:00-07
- Character
	- CHAR - comprimento fixo, se o USUÁRIO inserir, por exemplo, 3 letras e for um **CHAR(5)**, o PostgreSQL insere 2 espaços em branco.
	- VARCHAR - guarda quantidades variáveis de caracteres.
	- VARCHAR(40) - guarda até 40 caracteres, remove caracteres extras se necessário.
	- TEXT - guarda quantidades variáveis de caracteres.
- JSON
- Geometric
- Range
- Arrays
- Boolean
	- true, yes, on 1, t, y -> TRUE
	- false, no, off, 0, f, n -> FALSE
	- null -> NULL
- XML
- UUID

---

PS: No PostgreSQL, as diferenças entre os tipos `VARCHAR`, `CHAR` e `TEXT` **geralmente não afetam diretamente a performance**, mas há nuances que podem impactar indiretamente em cenários específicos. Vamos explorar:

### Similaridades entre `VARCHAR`, `CHAR` e `TEXT` no PostgreSQL:

1. **Implementação Interna**: No PostgreSQL, `VARCHAR` e `TEXT` compartilham a mesma implementação subjacente. Ambos armazenam strings com tamanho variável e têm overhead mínimo para gerenciar o tamanho dos dados.
2. **Desempenho Similar**: O desempenho de operações como leitura, escrita e busca para `VARCHAR` e `TEXT` tende a ser equivalente, pois ambos manipulam strings de maneira semelhante.

---

PS: Pode-se calcular valores entre datetime e interval, produzindo um novo datetime, assim como é possível usando o C#.