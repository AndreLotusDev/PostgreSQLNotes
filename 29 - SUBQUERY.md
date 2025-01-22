---
aliases: 
tags: 
date created: Thursday, January 16th 2025, 10:36:15 am
date modified: Wednesday, January 22nd 2025, 9:52:56 am
---
Subquery é ato de estruturar uma QUERY com finalidade unica em mais de uma QUERY, ao qual essas QUERIES são interdependente de si.

Por exemplo, entrar dentro de uma tabela e achar uma row, e baseado no valor dessa row filtrar as outras rows verificando se o valor é maior ou menor, isso só é possível como a estruturação lógica se propõe em duas etapas, portanto sendo necessário a construção de uma QUERY e SUBQUERY.

Outro exemplo, trazer clientes, mas somente os clientes com mais de 1000 pedidos efetuados.

```sql
SELECT name, email
FROM customers
WHERE id IN (
    SELECT customer_id
    FROM orders
    WHERE total_amount > 1000
);
```

---

PS: Subqueries podem ser utilizados em diversos locais dentro de uma QUERY, dentro do SELECT, FROM, JOIN, WHERE e muito mais.

---

## Correlated Subquery

Uma subquery co relacionada é quando uma query tem um alias e podemos usar este mesmo alias dentro da subquery, isso é muito útil para quando por exemplo, precisamos iterar a tabela e pegar seu valor maximo para cada tipo de uma especifica coluna.

Exemplo usando uma tabela FUNCIONARIOS em ingles:

```sql
SELECT e.EmployeeID, e.EmployeeName
FROM Employees e
WHERE e.Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE DepartmentID = e.DepartmentID
);
```