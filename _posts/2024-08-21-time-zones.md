---
layout: post
title: Временные зоны...
---

Получил на работе простую задачу - написать даг, для репликации таблицы с сервера на сервер. Таблица небольшая, штук шесть колонок - timestamp момента создания и несколько числовых полей. Забирать инкремент за предыдущее число. Написал, запустил - данные залились. Для проверки сделал группировку по дате, посмотреть количество за несколько последних дней. Неожиданно - не совпало. 

Смотрю какие строки вошли в конкретный день на разных серверах - строки одни и те же, а timestamp у них разный, разница между значениями часов. Причём забавный момент - запрос к базе через  ide, выбрать записи за конкретный день выдаёт одно количество, а такой же запрос из айрфлоу - уже другое. 

Часовые пояса. Как ни странно - первый раз за пять лет с этим сталкиваюсь, раньше везло - везде одинаковое локальное время было. 

Поменять локаль у БД не могу - прав нет, да и это 100% что-нибудь другое сломает. Попробовал ещё несколько вариантов - но всё не то. В итоге решил в лоб, через uglehack. Коряво, но задача решена. Надо будет почитать в свбободное время - какие best practices...
```sql
select
    id,
    created_dttm + interval'3hours' as created_dttm,
    field_1,
    field_2,
    field_3
from table_name
where 
    created_dttm >= '{{ ds }}'::timestamp - interval'8hours'
    and created_dttm < '{{ ds }}'::timestamp + interval'1day' - interval'8hours'
```