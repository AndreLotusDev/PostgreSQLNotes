---
aliases: 
tags: 
date created: quarta-feira, dezembro 18º 2024, 11:29:33 am
date modified: quarta-feira, dezembro 18º 2024, 11:40:08 am
---
Para adicionar uma foreign key, vamos supor, temos uma tabela PESSOA com dados basico da pessoa, nome, sobrenome, data de nascimento, cpf e temos uma tabela TRABALHADOR que tem uma foreign key para pessoa.

Exemplo: 

```sql
CREATE TABLE PESSOA (
    ID INT PRIMARY KEY,
    NOME VARCHAR(50),
    SOBRENOME VARCHAR(50),
    DATA_NASCIMENTO DATE,
    CPF VARCHAR(11)
);
```

```sql
CREATE TABLE TRABALHADOR (
    ID INT PRIMARY KEY,
    PESSOA_ID INT,
    FOREIGN KEY (PESSOA_ID) REFERENCES PESSOA(ID)
);
```
