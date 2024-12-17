---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 6:15:26 pm
date modified: sexta-feira, dezembro 13º 2024, 6:47:53 pm
---
Geralmente por boas práticas, nunca trazemos seja qual camada esteja em contato direto com o backend, service, api, consumer, etc e etc mas nunca trazemos todos os dados de uma vez, pois isso pode e vai sobrecarregar a sua internet, ainda mais se o número de requisições for muito grande, para isso usamos o WHERE e somente trazemos o necessário para tal camada.

Por exemplo, temos uma tabela de telefones, e iremos somente trazer os telefones com todas suas colunas somente os telefones que tem data de lançamento mais recente q o ano de 2022.

```sql
SELECT * FROM telefones WHERE data_lancamento > '2022-01-01';
```

Geralmente a ordem dos comandos se da por:
- SELECT configurando as colunas
- FROM selecionando a tabela
- WHERE filtrando por alguma coluna ou condição

---

Operadores que podemos usar no WHERE:

De igualdade:

```sql
SELECT * FROM clientes WHERE idade = 30;
```

De diferença:

```sql
SELECT * FROM clientes WHERE idade <> 30;
```

De menor que:

```sql
SELECT * FROM clientes WHERE idade < 30;
```


De maior que:

```sql
SELECT * FROM clientes WHERE idade > 30;
```

---

Podemos tornar o operador WHERE composto exigindo que mais de uma lógica seja executa ao mesmo tempo, com os operadores AND, NOT and OR.

```sql
SELECT * FROM clientes WHERE idade > 30 AND idade < 40;
```

```sql
SELECT * FROM clientes WHERE idade > 30 OR idade < 40;
```

```sql
SELECT * FROM clientes WHERE NOT idade > 30;
```

---

Também podemos usar operadores IN, NOT IN and BETWEEN.

```sql
SELECT * FROM clientes WHERE idade IN (30, 40);
```

```sql
SELECT * FROM clientes WHERE idade NOT IN (30, 40);
```

```sql
SELECT * FROM clientes WHERE idade BETWEEN 30 AND 40;
```

---

É possível dentro do WHERE fazer cálculos para se executar filtros.

```sql
SELECT * FROM clientes WHERE idade + 10 > 30;
```

Ou por exemplo, vamos filtrar somente cidades com densidade populacional maior que 6000.

```sql
SELECT * FROM cidades WHERE populacao / area > 6000;
```
