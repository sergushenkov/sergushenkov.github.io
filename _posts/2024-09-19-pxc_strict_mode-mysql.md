---
layout: post
title: PXC Strict Mode - жесткий контроль в MySQL
---

Есть даг, работающий с очередью тасков - запускает их сообразно своим критериям. Очередь хранится в таблицах внутри БД Airflow. Таблицы не [дефолтные](https://sergushenkov.github.io/there-is-always-another-way/), а специально созданные. Потребовалось расширить функционал - добавил ещё одну таблицу и получил неожиданную ошибку на операции INSERT:
```
MySQLdb.OperationalError: (1105, 'Percona-XtraDB-Cluster prohibits use of DML command on a table (airflow.dag_launcher_threads) without an explicit primary key with pxc_strict_mode = ENFORCING or MASTER')
```
pxc_strict_mode в зависимости от заданного режима определяет как БД будет относиться к предупреждениям и нештатным функциям:

`DISABLED` - не выполнять строгие проверки и работать в обычном режиме; ошибки или предупреждения при использовании экспериментальной/неподдерживаемой функции не регистрируются

`PERMISSIVE` - eсли проверка не пройдена, зарегистрируйте warning и продолжайте работу в обычном режиме

`ENFORCING` - если проверка не пройдена - отклонить операцию и выдать ошибку

`MASTER` - то же самое, что `ENFORCING`, за исключением того, что проверка явной блокировки таблицы не выполняется

Узнать, текущий режим на сервере:

```sql
mysql> SHOW VARIABLES LIKE "pxc_strict_mode";

Variable_name  |Value    |
---------------+---------+
pxc_strict_mode|ENFORCING|
```
Режим можно поменять (в ущерб надёжности)
```sql
mysql> SET GLOBAL pxc_strict_mode=DISABLED; 
```
но лучше дать mySQL то, что она ожидает:
```sql
mysql> ALTER TABLE dag_launcher_threads ADD PRIMARY KEY (run_id);
```