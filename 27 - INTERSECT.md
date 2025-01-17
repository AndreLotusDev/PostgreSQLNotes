---
aliases: 
tags: 
date created: Thursday, January 16th 2025, 10:06:31 am
date modified: Thursday, January 16th 2025, 10:13:09 am
---
Quando usamos o INTERSECT como KEYWORD estamos tentando executar uma tarefa que é o oposto do UNION, estou analisando dois data source e filtrando somente pelo que tem em comum, por isso é importante as duas tabelas terem as mesmas colunas, e essas colunas terem o mesmo data type.

---

Um exemplo de usabilidade dessa KEYWORD é quando temos numa tabela vários usuários, por exemplo uma tabela de permissao, so que por algum motivo essa tabela de permissao para elencar todas as permissoes um usuário é elencado em várias ROWS, podemos fazer da seguinte forma para mapear um usuário com permissão de leitura e escrita ao mesmo tempo.

```sql
SELECT user_id 
FROM user_permissions 
WHERE permission = 'READ'
INTERSECT
SELECT user_id 
FROM user_permissions 
WHERE permission = 'WRITE';
```