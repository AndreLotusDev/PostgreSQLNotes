---
aliases: 
tags: 
date created: Sunday, February 9th 2025, 4:01:21 pm
date modified: Sunday, February 9th 2025, 5:14:55 pm
---
Transações são importantes para executar inserções, deleções, atualizações em múltiplas tabelas, mas ao mesmo tempo fazendo isso com a certeza que somente ira atualizar os dados em todas as tabelas ao mesmo tempo se todas as operações forem consistentes e não devolverem um erro, se durante a operação de contexto fechado no meio da transação a etapa 3 não funcionar, ele não só desfazer a operação 3, como a 2 e 1 assim garantindo consistencia de dados.

A transação pode ser muito útil por exemplo na transação de duas contas bancárias, eu só atualizo o valor da conta bancaria 1 si e somente se a conta 2 poder de fato receber aquele valor.

Imagina se você perder o valor da sua conta ao realizar uma transferencia, e ficar sabendo q essa transferencia nao pode ser performada e portanto esse dinheiro ficar no limbo e portanto ser necessário a comunicação com um time técnico do banco.

---

PS: Ou seja, toda transação deve ter a KEYWORD BEGIN no começo da operação e COMMIT no final, caso não tenha o COMMIT, tudo feito dentro da clausula depois da PALAVRA BEING não é salvo dentro do banco de dados.

Exemplo:  

```sql
CREATE TABLE accounts (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    balance DECIMAL NOT NULL
);

INSERT INTO accounts (name, balance) VALUES ('Alice', 1000.00);
INSERT INTO accounts (name, balance) VALUES ('Bob', 500.00);

BEGIN;  

UPDATE accounts SET balance = balance - 100 WHERE name = 'Alice';
UPDATE accounts SET balance = balance + 100 WHERE name = 'Bob';

-- COMMIT;
```

PS: Nesse exemplo, como eu esqueço o commit, a tabela contas ainda permanecera os dados antigos, onde alice ainda tem 1000 reais e bob tem 500 reais.

Para evitar isso, basta:

```sql
BEGIN;  -- Start the transaction

UPDATE accounts SET balance = balance - 100 WHERE name = 'Alice';
UPDATE accounts SET balance = balance + 100 WHERE name = 'Bob';

COMMIT;  -- Commit the transaction to save changes
```

---

Lembre sempre de ter código defensivo para fechar a transação, caso contrário algumas se caso ocorrer erro podem ficar dependuradas gerando gargalo no sistema.