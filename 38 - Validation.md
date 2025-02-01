---
aliases: 
tags: 
date created: Friday, January 24th 2025, 9:06:45 am
date modified: Monday, January 27th 2025, 9:41:56 pm
---
Temos algumas formas de se validar a nível de linha (row) uma tabela de banco de dados, tais quais:

- Um valor é dado (não nulo)?
- O valor é único em sua coluna?
- O valor é >, <, >=, <=, = a outro valor?

---

Os validadores de NULL são importantes pois garante que de acordo com as regras de negócio não adicionemos ROWS que não estão em conformidade com as regras de negócio, assim como garante a integridade, qualidade dos dados e evita que ROWS sem sentido cheguem ao banco de dados.

Há também a possibilidade de adicionar não somente validadores de NULL, mas também colocar valores DEFAULT para situações onde o usuário possa esquecer de inputar o valor correto.

É possível também criar validações multicolunares [[Queries]]

---

Podemos fazer check validation, check validation checam se o valor inserido numa coluna esta correto ou de acordo com as regras, por exemplo, podemos checar se o PRECO dentro da tabela de produtos é maior que 0.

[[2 - Check]]

```sql
ALTER TABLE produtos
ADD CHECK (preco > 0);
```

Também é possível checar multiplas colunas de uma vez so.

```sql
create table deliverable (
id serial primary key,
dispatched date,
delivered date
)

alter table deliverable
add check (dispatched < delivered);

insert into deliverable (dispatched, delivered) values (now(), NOW() - INTERVAL '1 day');
```

---

- Regras a cerca de validações do valores que provavelmente irão mudar constantemente: não fazer do lado do banco de dados.
- Regras de validação do valor que são muito complexas: não fazer do lado do banco de dados.
- Nós queremos ter certeza que o valor correto está inserido ou valores de dominio: Insira validação no banco de dados.

