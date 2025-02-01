---
aliases: 
tags: 
date created: Thursday, January 30th 2025, 9:05:26 am
date modified: Thursday, January 30th 2025, 9:10:48 am
---
**Podemos verificar o tamanho de uma tabela e o quanto ela usa dentro do OS com o seguinte comando:**

SELECT pg_size_pretty(pg_relation_size('users'));
SELECT pg_size_pretty(pg_table_size('table_name')) AS table_size;

---

**Também podemos printar quanto de espaço é ocupado pelo index da tabela, com o seguinte comando:**

SELECT pg_size_pretty(pg_relation_size('users_username_idx'));
SELECT pg_size_pretty(pg_indexes_size('table_name')) AS indexes_size;

---

**Para calcular o tamanho do TOAS (se tem):**

SELECT pg_size_pretty(pg_table_size('pg_toast.pg_toast_' || reltoastrelid::regclass)) AS toast_size
FROM pg_class
WHERE relname = 'table_name';

---

**Quebra de informação por setor (index, tabela, TOAST):**

SELECT
    pg_size_pretty(pg_table_size('table_name')) AS table_size,
    pg_size_pretty(pg_indexes_size('table_name')) AS indexes_size,
    pg_size_pretty(pg_total_relation_size('table_name') - pg_table_size('table_name') - pg_indexes_size('table_name')) AS toast_size,
    pg_size_pretty(pg_total_relation_size('table_name')) AS total_size;

---

**Para calcular o tamanho total:**

SELECT pg_size_pretty(pg_total_relation_size('table_name')) AS total_size;

---

**Tamanho de todas as tabelas no banco:**

SELECT
    table_schema,
    table_name,
    pg_size_pretty(pg_total_relation_size(table_schema || '.' || table_name)) AS total_size
FROM information_schema.tables
WHERE table_schema NOT IN ('pg_catalog', 'information_schema')
ORDER BY pg_total_relation_size(table_schema || '.' || table_name) DESC;

---

**Tamanho de todos os indexes no banco:**

SELECT
    indexrelid::regclass AS index_name,
    pg_size_pretty(pg_relation_size(indexrelid)) AS index_size
FROM pg_index
ORDER BY pg_relation_size(indexrelid) DESC;