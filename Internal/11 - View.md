---
aliases: 
tags: 
date created: Friday, February 7th 2025, 10:56:36 am
date modified: Sunday, February 9th 2025, 3:26:28 pm
---
Quando temos uma situação que uma determinada subquery a usamos muitas vezes, podemos provavelmente isolar ela em uma VIEW que podemos chamar inumeras vezes em diferentes tipos de QUERY, facilitando legibilidade, capacidade de dar manutenção e outras coisas.

Assim como o CTE (Common Table Expression), o VIEW funciona de forma similar ao qual podemos usar ele em diversos lugares.

A view pode guardar uma tabela inteira, um pedaço com where da tabela, a mistura de varias tabelas.

---

Podemos pensar então uma VIEW como uma pecinha de lego que voce pode usar ela várias vezes em cenários diferentes para facilitar e aumentar a produtividade durante a criação de queries e manutenção de sistemas.

---

Exemplo de uma query ao qual combina a quantidade de produtos vendidos e filtra pode produto da categoria da TI:

```sql
CREATE VIEW it_products_sold AS
SELECT 
    p.product_id,
    p.product_name,
    p.product_type,
    sp.sale_id,
    sp.sale_date,
    sp.quantity_sold,
    sp.total_amount
FROM 
    product p
JOIN 
    selled_product sp 
ON 
    p.product_id = sp.product_id
WHERE 
    p.product_type = 'IT Product';
```

Também podemos usar a VIEW para performar JOINS:

```sql
CREATE VIEW electronics_products AS
SELECT 
    product_id,
    product_name,
    product_type,
    price
FROM 
    product
WHERE 
    product_type = 'Electronics';

CREATE VIEW customer_electronics_purchases AS
SELECT 
    c.customer_id,
    c.customer_name,
    ep.product_name,
    ep.price,
    sp.sale_date,
    sp.quantity_sold,
    sp.total_amount
FROM 
    electronics_products ep
JOIN 
    selled_product sp 
ON 
    ep.product_id = sp.product_id
JOIN 
    customer c 
ON 
    sp.customer_id = c.customer_id;
```

Podemos alterar e deletar uma VIEW da seguinte forma:

Você dropar a view da seguinte forma:

```sql
DROP VIEW view_name;
```

PS: Todavia dessa forma gera erro caso a VIEW não exista, portanto podemos escrever esse mesmo comando de forma defensiva:

```sql
DROP VIEW IF EXISTS view_name;
```

A mesma coisa com o update:

```sql
REPLACE VIEW view_name AS
{NEW_QUERY_FORMAT}
```

Todavia também podemos usar a sintaxe defensiva:

```sql
CREATE OR REPLACE VIEW view_Name AS 
{NEW_QUERY_FORMAT}
```