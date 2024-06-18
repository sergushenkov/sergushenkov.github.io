---
layout: post
title: CУБД - реляционные и/или колоночные?
---

На каком то недавнем техинтервью с той стороны прозвучало противопоставление реляционных и колоночных СУБД. Я сказал своё мнение что одно другому не мешает, и дальше как то переключились на другой вопрос. А сегодня наткнулся в [ТГ](https://t.me/boris_again/2286) на вопрос "В чем разница между реляционными и колоночными БД?"

Реляционные – содержат информацию в виде таблиц, которые могут быть связаны между собой. Ну и как этот факт может отменить способ записи данных таблицы в файл на диске, наличие сжатия/шифрования или ещё что-то подобное? Это влияет на производительность в конкретных запросах, может влиять на план выполнения, но для пользователя полностью скрыто под капотом. Юзер всё также использует таблицы, связывая их друг с другом.

В Greenplum можно указать для одной и той же таблицы хоть колоночное, хоть строковое хранение. И что, от этого она перестаёт быть реляционной?