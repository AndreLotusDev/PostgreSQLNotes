---
aliases: 
tags: 
date created: segunda-feira, dezembro 16º 2024, 10:38:23 am
date modified: segunda-feira, dezembro 16º 2024, 11:55:25 am
---
Temos quatro tipos de relacionamento

Muitos para um
Muitos para muitos
Um para muitos
Um para um

---

Primary key: Identificador único na tabela para achar um elemento dentro da tabela.

Foreign key: É um ponteiro dentro da tabela que referência um elemento dentro de outra tabela.

PS: Não necessariamente precisa ser somente uma coluna, pode ser um conjunto de colunas, por exemplo que forma uma primary key.

---

Exemplo de uma PK e FK composta:

```sql
-- Criação da tabela 'departamentos' com chave primária composta
CREATE TABLE departamentos (
    id_empresa INTEGER,
    id_departamento INTEGER,
    nome_departamento VARCHAR(100),
    PRIMARY KEY (id_empresa, id_departamento)
);

-- Criação da tabela 'funcionarios' com foreign key composta
CREATE TABLE funcionarios (
    id_funcionario SERIAL PRIMARY KEY,
    nome_funcionario VARCHAR(100),
    id_empresa INTEGER,
    id_departamento INTEGER,
    cargo VARCHAR(50),
    -- Definição da foreign key composta
    FOREIGN KEY (id_empresa, id_departamento)
        REFERENCES departamentos(id_empresa, id_departamento)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
```