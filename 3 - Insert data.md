---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 5:43:48 pm
date modified: sexta-feira, dezembro 13º 2024, 5:48:26 pm
---
Para inserir dados no PostgreSQL podemos usar a clausula INSERT INTO NOME_DATA_TABELA (colunas) VALUES (valores)

---

Exemplo, temos uma tabela com id, nome da cidade, e país da cidade. Podemos executar o seguinte SQL de insert.

```sql
INSERT INTO cities (name, country) VALUES ('São Paulo', 'Brasil');
```

Para inserir mais de um valor sem ter que ficar repetindo a clausula INSERT INTO podemos fazer da seguinte maneira:

```sql
INSERT INTO cities (name, country) VALUES ('São Paulo', 'Brasil'), ('Rio de Janeiro', 'Brasil'), ('Buenos Aires', 'Argentina');
```

Perceba que podemos separar por vírgulas e por parenteses cada insert.