---
layout: post
title: Мидл - Сбер
---

![](/./images/2024-06-30-middle-sber.png)

В Сбере я проработал полтора года - с октября 2020 по апрель 2022. Поработал и в башне на Оружейном и в башнях на Кутузовском - до сих пор гуляя в тех краях, высматриваю знакомые силуэты.

Было по разному, в целом - хорошее впечатление, если по деньгам будет интересное предложение - задумаюсь. Поработал в нескольких командах - искал где интересней стек инструментов.

Первая место - перекладывали данные между Teradata и Greenplum, реализовывали свою версию Data Quality, инструменты - Informatica PowerCenter и хранимые процедуры на PL/SQL. Процедуры писать было интересно, а вот Infromatica - разочаровала. Дорогой, красивый, простой, но жутко скучный инструмент - думать не надо. Команда была классная - с парой человек оттуда до сих пор периодически общаемся, тимлид кстати по характеру - вылитый [Тед Лассо](https://www.kinopoisk.ru/series/1309707) :)

Второе место - перекладывал данные для DS между Teradata, Greenplum и Hadoop. Достаточно быстро выяснилось, что эта моя работа уже неактуальна - параллельная команда работала над удобным инструментом подписки на данные, где всё это делалось в автоматическом режиме. Никто не гнал, какая-то работа всегда бы нашлась, но ощущение невостребованности заставило искать новые вакансии.

*Из того что запомнилось на этом этапе - подготовил "учебник" по CTL. Airflow по факту инструмент №1 для автоматизации ETL, его практически все знают и умеют на базовом уровне. Но, по стандартам безопасности, он хотя и не был под запретом на серверах, но "нежелательно использовать", соответственно поддержки никакой. Есть внутренний инструмент CTL - простой, закрывающий большую часть потребностей, но совершенно ненаглядный и без нормальной документации. Мне поставили задачу - подготовить своего рода "учебник", чтобы человек знающий airflow мог быстро начать работать с CTL. Я сделал репозиторий с примерами основных задач - как это можно решать средствами CTL. Сразу особого отклика не получил, но тем приятнее было получить отклик, когда уже полтора года как не работал в Сбере :)*

![](/./images/2024-06-30-middle-sber-2.png)

Третья место - самая большая надежда, хороший челендж и три важных урока. Вакансию увидел на слаке ODS (Open Data Science), хорошая вилка (даже нижняя граница процентов на 15 выше моей зарплаты на тот момент), очень интересный стек, который было интересно попробовать - scala и spark. Опыта по инструментам не было от слова совсем, но откликнулся. На собеседовании честно сказал и про отсутствие опыта, и про свою мотивацию, поотвечал на вопросы по python/sql/hadoop, и в общем то особо не надеялся, что подойду им. Неожиданно - подошёл. Как я потом понял - потому что вилка зарплаты не заинтересовала скалистов :) , но для меня это был хороший шаг вперёд.

В первый рабочий день выяснилось, что меня берут не на расширение команды, а на замену уходящему дата-инженеру, который сегодня последний день в команде :) . **Урок №1 - спрашивай на собесах, почему открылась вакансия.** 

Т.е. есть идея продукта на scala/spark, который нужно реализовать, но знаний по стеку нет и учиться не у кого. Огромное спасибо это самому дата-инженеру, что она и после ухода продолжала общаться со мной, объясняя требуемую логику - и я допилил продукт :) Выпустить релиз на прод - это вообще был отдельный квест, но тоже получилось.

В общем, был шанс дальше расти в Сбере, но не сложилось. Первая причина - война, часть команды после февраля 2022 ушла из Сбера, оставшимся собирались предложить варианты в других командах. Вторая по порядку (но основная по важности) причина - деньги. Ту самую вилку из объявления я не получил - тема зарплаты на собесах не поднималась, я был уверен что нижние цифры в объявлении практически оффер (и возможно человек со стороны их бы и получил). В первый месяц не получив прибавку - решил что она появится после испытательного срока, продолжил работать. **Урок №2 - по деньгам никаких умолчаний быть не должно, всё надо проговаривать и фиксировать договоренности.** После окончания испытательного - денег больше не стало, пришёл с вопросом к тимлиду. Озвучил свои ожидания, он помочь ничем не смог - объявление давал не он, а тот самый дата-инженер который уволился. В принципе вилка такая и была, но так как я уже был в Сбере и со своим грейдом в эту вилку не вписывался, то остался при своих. Грейд есть шанс повысить, но дело это небыстрое. Просто так, в ходе внутренней ротации, грейд не повышают. В принципе это понятно - чтобы команды внутри Сбера не переманивали сотрудников друг у друга, но как работнику - досадно.

Поразмыслив, вспомнил, что перед Новым годом собеседовался в Тинькофф, и в принципе мы оставили друг у друга хорошее впечатление, снова позвонил туда. Так начался новый этап в моей карьере.
**Урок №3 - надо регулярно ходить на собесы, даже если прямо сейчас не ищешь работу.**