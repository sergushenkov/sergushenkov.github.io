---
layout: post
title: Хардкодим sql-строки
---

В решении sql-задачек удобно, когда есть возможность выполнить запрос и посмотреть, что в итоге получается. Стандартный ход в этой ситуации - создать таблички, возможно темповые, и гонять на них - но лень...

В PostgreSQL, на случай если необходимо захардкодить несколько строк данных, есть удобная команда - https://postgrespro.ru/docs/postgresql/9.6/sql-values, которая просто просится в CTE для таких случаев:

```sql
with t1 (id, describe, dttm) as (  -- таблица из двух строк
    values 
        (1, 'any text', now()), 
        (2, 'some text', '2024-01-01'::timestamp)
)
select max(dttm) from t1
```

Неожиданно, но в Vertica такого нет и проблема решается громоздким вариантом через union:

```sql
with t1 as (  -- таблица из двух строк
    select 1 as id, 'any text' as describe, now() as dttm
    union all
    select 2, 'some text', '2024-01-01'::timestamp
)
select max(dttm) from t1
```