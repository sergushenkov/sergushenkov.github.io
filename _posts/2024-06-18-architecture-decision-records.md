---
layout: post
title: Мышление письмом - ADR
---

Всегда любил писать тексты (хотя, честно скажу, не всегда на это были силы и время). Потому что мысли забываются, и это бывает обидно :) Да и видя предыдущие шаги текстом перед глазами - легче развивать мысль. 

Вселенная отзывается на интерес - и регулярно попадались материалы про ведение дневника, [письменные практики](https://pismennyepraktiki.com/base), утренние страницы, [мышление письмом](https://ailev.livejournal.com/1513051.html). После перехода в IT выяснилось, что и тут есть подобное. Потому что люди везде одинаковы, и то, что работает в одной сфере, скорее всего будет работать и в другой. 

Одна из таких практик - ADR - Architecture Decision Records. Суть в том, что принимая какое то решение, мы делаем запись об этом - почему возник такой вопрос, какие варианты решения были и что и почему в итоге выбрали?

Что-то похожее я делал, но очень коротко, не особо осознанно и бессистемно - либо комментариями прямо в коде, либо многострочным комментарием в начале. Обычно в формате "мой вопрос - ответ от заказчика". Цель этого было аргументировать неочевидные решения, на случай возможных "разборов полёта". Выглядит примерно так (отредактированный вариант, чтобы СБ не ругался :) ):

```
. abc.cabcname as abcount_name - везде null
  . для тестового контура это поле затёрто, т.к. там могут быть клиентские данные 
. abc.cabcbvb as chapter_code - в таблице указано четыре возможных значения в этом поле, у нас таких только три (буквы Т нет)
  . сейчас это нормально, но в код лучше заложить, если вдруг появятся
. Для двух полей - distributed_group и customer_key - в качестве данных мы берём одно и то же - abc.iabccus, но тип полей в вики указан разный - smallint и bigint. Smallint изменил на int - иначе данные не влезали, для smallint макс. значение 32000 с копейками, по факту там больше
  . select max(abc.iabccus) from ods.abc;  -- 123456789
  . mod(abc.iabccus, 32767)::smallint as distributed_group - письмо от Романа, 3 июня
. если abc.dabclose < 01.01.2024 делаем одну запись с ACTUAL_START_DATE = 01.01.2024, ACTUAL_END_DATE = 31.12.2024
  если abc.dabclose >= 01.01.2024 and abc.cabcprizn != 'З' делаем одну запись ACTUAL_START_DATE = abc.dabclose, ACTUAL_END_DATE = 31.12.2024
  если abc.dabclose >= 01.01.2024 and abc.cabcprizn = 'З' делаем две записи.
  ACTUAL_START_DATE = greatest(abc.dabcopen, 01.01.2024), ACTUAL_END_DATE = dabcclose-1, CLOSE_DATE = null
  ACTUAL_START_DATE = dabcclose, ACTUAL_END_DATE = 31.12.2024, CLOSE_DATE = dabcclose
. 5 записей (iabccus in (XXXXXX, YYYYYY, ZZZZZZ, VVVVVV, WWWWWW)) имеют dabcclose = '2030-01-01' и cabcprizn = 'З' - не попадают в партицию abc
  . давай их грохнем из реплики. по ним не было никаких движений, они в реальности скорее всего в 2010 году закрыты
```

А на этой неделе начал читать в [ТГ канале Chernov sharit](https://t.me/chernov_sharit) большую [подборку материалов про ADR](https://t.me/chernov_sharit/536), в том числе ссылки на [шаблоны](https://vanadium23.me/openbox/quotes/202302061404/). Понравилось. Попробую делать "по-взрослому"