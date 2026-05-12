# Базы данных

## Содержание
- [Базы данных](#базы-данных)
  - [Содержание](#содержание)
- [Реляционная модель](#реляционная-модель)
  - [Основные принципы](#основные-принципы)
- [Разделы SQL](#разделы-sql)
  - [DDL - Data Definition Language (язык определения данных)](#ddl---data-definition-language-язык-определения-данных)
    - [Основные операторы:](#основные-операторы)
  - [DML - Data Manipulation Language (язык манипулирования данными)](#dml---data-manipulation-language-язык-манипулирования-данными)
    - [Основные операторы:](#основные-операторы-1)
  - [DCL - Data Control Language (язык управления доступом)](#dcl---data-control-language-язык-управления-доступом)
    - [Основные операторы:](#основные-операторы-2)
  - [TCL - Transaction Control Language (язык управления транзакциями)](#tcl---transaction-control-language-язык-управления-транзакциями)
    - [Основные операторы:](#основные-операторы-3)
- [Установка PostgreSQL](#установка-postgresql)
- [Типы данных в PostgreSQL](#типы-данных-в-postgresql)
  - [Числовые](#числовые)
  - [Символьные](#символьные)
  - [Логический тип](#логический-тип)
  - [Дата и время](#дата-и-время)
  - [Двоичные данные](#двоичные-данные)
  - [Типы для идентификаторов и структур](#типы-для-идентификаторов-и-структур)
  - [Пространственные и специальные типы](#пространственные-и-специальные-типы)
- [Схемы](#схемы)
- [Оператор SELECT](#оператор-select)
  - [Выбор отдельных столбцов](#выбор-отдельных-столбцов)
  - [Операторы сравнения в WHERE](#операторы-сравнения-в-where)
    - [Основные операторы](#основные-операторы-4)
  - [Оператор BETWEEN](#оператор-between)
  - [Оператор IN / NOT IN](#оператор-in--not-in)
  - [Оператор LIKE / ILIKE](#оператор-like--ilike)
    - [LIKE](#like)
    - [ILIKE](#ilike)
    - [Escape последовательности в LIKE / ILIKE](#escape-последовательности-в-like--ilike)
- [Оператор LIMIT](#оператор-limit)
- [Оператор ORDER BY](#оператор-order-by)
- [Оператор GROUP BY](#оператор-group-by)
  - [Агрегатные функции](#агрегатные-функции)
- [Условия фильтрации с HAVING](#условия-фильтрации-с-having)
- [Primary Key](#primary-key)
- [Foreign Key](#foreign-key)
- [Проектирование схемы БД](#проектирование-схемы-бд)
  - [Этапы проектирования](#этапы-проектирования)
  - [Типовые связи](#типовые-связи)
  - [Нормальные формы](#нормальные-формы)
    - [1NF - Первая нормальная форма](#1nf---первая-нормальная-форма)
    - [2NF - Вторая нормальная форма](#2nf---вторая-нормальная-форма)
    - [3NF - Третья нормальная форма](#3nf---третья-нормальная-форма)
- [JOIN](#join)
- [Вложенный запрос](#вложенный-запрос)
  - [Типы вложенных запросов](#типы-вложенных-запросов)
    - [Скалярный подзапрос](#скалярный-подзапрос)
    - [Подзапросы с IN / ANY / ALL](#подзапросы-с-in--any--all)
    - [Подзапросы в FROM (табличные подзапросы)](#подзапросы-в-from-табличные-подзапросы)
    - [Коррелированный подзапрос](#коррелированный-подзапрос)
- [CTE](#cte)
- [Оператор CASE](#оператор-case)
- [Изменение таблиц и удаление данных](#изменение-таблиц-и-удаление-данных)
  - [Команда ALTER TABLE](#команда-alter-table)
    - [Добавление столбца](#добавление-столбца)
    - [Добавление столбца с указанием значения по умолчанию](#добавление-столбца-с-указанием-значения-по-умолчанию)
    - [Удаление столбца](#удаление-столбца)
    - [Изменение типа столбца явно](#изменение-типа-столбца-явно)
    - [Обновление данных в существующей таблице](#обновление-данных-в-существующей-таблице)
    - [Переименование таблицы](#переименование-таблицы)
    - [Переименование столбца](#переименование-столбца)
  - [Команда DELETE](#команда-delete)
- [EXPLAIN и EXPLAIN ANALYZE](#explain-и-explain-analyze)
- [Индексы](#индексы)
  - [Зачем нужны индексы?](#зачем-нужны-индексы)
  - [Когда индексы НЕ нужны?](#когда-индексы-не-нужны)
  - [Основные типы индексов в PostgreSQL](#основные-типы-индексов-в-postgresql)
    - [B-tree индекс](#b-tree-индекс)
    - [Hash индекс](#hash-индекс)
    - [GIN индекс](#gin-индекс)
- [Представления VIEW](#представления-view)
  - [Materialized VIEW](#materialized-view)
- [Сложные типы данных](#сложные-типы-данных)
  - [JSON / JSONB](#json--jsonb)
  - [ARRAY](#array)
- [Расширения PostgreSQL](#расширения-postgresql)
  - [PostGIS](#postgis)
  - [pg\_trgm](#pg_trgm)
- [Основные параметры конфигурации PostgreSQL](#основные-параметры-конфигурации-postgresql)
- [Транзакции, блокировки и параллелизм в PostgreSQL](#транзакции-блокировки-и-параллелизм-в-postgresql)
  - [Зачем нужны транзакции](#зачем-нужны-транзакции)
  - [ACID - фундамент транзакций](#acid---фундамент-транзакций)
  - [BEGIN / COMMIT / ROLLBACK](#begin--commit--rollback)
  - [Уровни изоляции транзакций](#уровни-изоляции-транзакций)
    - [Read Committed](#read-committed)
    - [Repeatable Read](#repeatable-read)
    - [Serializable](#serializable)
  - [MVCC - Multi-Version Concurrency Control](#mvcc---multi-version-concurrency-control)
  - [Как PostgreSQL видит данные?](#как-postgresql-видит-данные)
  - [Блокировки в PostgreSQL](#блокировки-в-postgresql)
    - [Типы блокировок](#типы-блокировок)
      - [Row-level блокировки](#row-level-блокировки)
      - [Table-level блокировки](#table-level-блокировки)
    - [Deadlock (Взаимная блокировка)](#deadlock-взаимная-блокировка)
    - [Просмотр блокировок](#просмотр-блокировок)
    - [SELECT FOR UPDATE](#select-for-update)
- [Совместный доступ: пессимистическая и оптимистическая модели](#совместный-доступ-пессимистическая-и-оптимистическая-модели)
  - [Оптимистическая модель](#оптимистическая-модель)
  - [Пессимистическая модель](#пессимистическая-модель)
- [Курсоры](#курсоры)
- [Введение в NoSQL](#введение-в-nosql)
  - [CAP-теорема](#cap-теорема)
- [Redis](#redis)
  - [Запуск](#запуск)
  - [Команды](#команды)


# Реляционная модель
`Реляционная модель` - это способ представления данных в виде таблиц (отношений). Каждая таблица описывает объекты одного типа (например, студенты, курсы, заказы).

## Основные принципы
- Данные организованы в таблицы (отношения).
- Таблицы состоят из строк (кортежей) и столбцов (атрибутов).
- Каждая таблица имеет первичные ключ, однозначно определяющий каждую запись.

| ID студента   | Имя       | Факультет     | Год поступления   |
|-              |-          |-              |-                  |
| 1             | Анна      | ИТ            | 2023              |
| 2             | Дмитрий   | Экономика     | 2022              |
| 3             | Елена     | ИТ            | 2023              |

- `Отношение` - таблица данных.
- `Атрибут` - столбец таблицы, характеризующий объект.
- `Кортеж (tuple)` - строка таблицы, отдельный экземпляр объекта. 
- `Домен` - множество допустимых значений для атрибута.
- `Ключ (key)` - минимальный набор атрибутов, уникально определяющих кортеж.
- `Внешний ключ (foreign key)` - ссылка на ключ другой таблицы (связь между отношениями).

# Разделы SQL

## DDL - Data Definition Language (язык определения данных)

Создание и изменение структуры БД.

### Основные операторы:
1. `CREATE` - создание таблиц, схем, индексов.
2. `ALTER` - изменение структуры объектов.
3. `DROP` - удаление объектов.

## DML - Data Manipulation Language (язык манипулирования данными)

Создание и изменение структуры БД.

### Основные операторы:
1. `SELECT` - выборка данных.
2. `INSERT` - добавление записей.
3. `UPDATE` - изменение данных.
4. `DELETE` - удаление данных.

## DCL - Data Control Language (язык управления доступом)

Управление правами пользователей.

### Основные операторы:
1. `GRANT` - предоставление прав.
2. `REVOKE` - отзыв прав.

## TCL - Transaction Control Language (язык управления транзакциями)

Управление выполнением групп операций.

### Основные операторы:
1. `COMMIT` - фиксация изменений.
2. `ROLLBACK` - отмена изменений.
3. `SAVEPOINT` - создание точки отката.

# Установка PostgreSQL

Запуск PostgreSQL в контейнере:

```bash
docker run --name pg -e POSTGRES_USER=myuser -e POSTGRES_PASSWORD=mysecret
-e POSTGRES_DB=mydb -p 5432:5432 -d postgres:16
```

Подключение к БД в терминале:

```bash
psql "host=localhost port=5432 dbname=mydb user=myuser password=mysecret"
```

Выход из psql:

```bash
\q
```

В pgadmin:

```bash
Servers->Register->Server
Name->DB (название в pgadmin)
Connection->address->127.0.0.1
Username->myuser
Password->mysecret
Save
```

# Типы данных в PostgreSQL

## Числовые

| Тип                               | Описание                  | Пример        | 
|-                                  |-                          |-              |     
| `smallint`                        | целое число (2 байта)     | 32767         |                  
| `integer` / `int`                 | целое число (4 байта)     | 100000        |                 
| `bigint`                          | целое число (8 байт)      | 9000000000    |
| `decimal(p,s)` / `numeric(p,s)`   | фиксированная точность    | 12.34         |
| `real`                            | число с точкой (4 байта)  | 3.14          | 
| `double precision`                | число с точкой (8 байт)   | 2.71828       | 
| `serial`, `bigserial`             | автоинкрементные целые    | 1, 2, 3...    |

## Символьные

| Тип           | Описание                | Пример                  | 
|-              |-                        |-                        |     
| `char(n)`     | фиксированная длина     | 'ABC'                   |                  
| `varchar(n)`  | переменная длина (до n) | 'Привет'                |                 
| `text`        | произвольная длина      | 'Длинная строка текста' |

## Логический тип

| Тип           | Описание                | Пример                  | 
|-              |-                        |-                        |     
| `boolean`     | логическое значение     | TRUE, FALSE             |  

## Дата и время

| Тип           | Описание                      | Пример                    | 
|-              |-                              |-                          |     
| `date`        | календарная дата              | 2025-11-10                |                  
| `time`        | время суток                   | 14:30:00                  |                 
| `timestamp`   | дата и время                  | 2025-11-10 14:30:00       |
| `timestamptz` | дата и время с часовым поясом | 2025-11-10 14:30:00+03    |
| `interval`    | промежуток времени            | 2 days 3 hours            |

## Двоичные данные

| Тип           | Описание                | Пример                  | 
|-              |-                        |-                        |     
| `bytea`       | двоичные данные         | \\xDEADBEEF             |

## Типы для идентификаторов и структур

| Тип               | Описание              | Пример            | 
|-                  |-                      |-                  |     
| `uuid`            | универсальный уникальный идентификатор    | 3ccaab7d-e128-4b1a-9f1d-abd316ea2056                            |                  
| `json`, `jsonb`   | хранение JSON-данных  | {"имя":"Анна"}    |                 
| `xml`             | XML-данные            | <data>text</data> |
| `array`           | массивы знаечний      | {1, 2, 3}         |

## Пространственные и специальные типы

| Тип                                               | Описание                  | 
|-                                                  |-                          |    
| `point`, `line`, `path`, `box`, `circle`, `lseg`  | геометрические типы                                                                            |                  
| `lnet`, `cidr`, `macaddr`                         | сетевые адреса            |                
| `money`                                           | денежный тип              |
| `tsvector`, `tsquery`                             | полнотекстовый поиск      |

# Схемы

| Postgres  | mydb              | Students  | 
|-          |-                  |-          |     
|           | public students   |           |
|           | bmstu students    |           |

По умолчанию Postgres создает таблицы в схеме `public`. Схема является аналогом __пространства имен__.

```sql
CREATE SCHEMA bmstu;
```

# Оператор SELECT

`SELECT` - основной оператор SQL для выборки данных из таблицы.

```sql
SELECT столбцы
FROM таблица
[WHERE условие]
[GROUP BY столбец]
[HAVING условие_группы]
[ORDER BY столбец [ASC|DESC]]
[LIMIT n];
```

`DISTINCT` - ключевое слово для возврата только __уникальных значений__.

## Выбор отдельных столбцов

```sql
SELECT столбец1, столбец2, ...
FROM имя_таблицы;
```

## Операторы сравнения в WHERE

Используются для фильтрации строк по значениям столбцов.

### Основные операторы
- `=` - равно
- `<>` или `!=` - не равно
- `>` - больше
- `<` - меньше
- `>=` - больше или равно
- `<=` - меньше или равно

```sql
WHERE age = 30
WHERE salary >= 50000
WHERE price <> 0
WHERE created_at < '2024-01-01'
```

## Оператор BETWEEN

Фильтрует значения, которые находятся в диапазоне (__включительно__).

```sql
WHERE значение BETWEEN нижняя_граница AND верхняя_граница
WHERE price BETWEEN 100 AND 500
WHERE test_date BETWEEN '2024-01-01' AND '2024-12-31'
WHERE test_name BETWEEN 'A' AND 'M'
```

## Оператор IN / NOT IN

`IN` и `NOT IN` применяются для фильтрации строк по списку значений.

```sql
SELECT *
FROM employees
WHERE department_id IN (10, 20, 30);

SELECT *
FROM products
WHERE category_id NOT IN (2, 4, 6);
```

## Оператор LIKE / ILIKE

Используются для поиска строк по шаблону (__pattern matching__).

### LIKE
- Чувствителен к __регистру__
- Поддерживает спецсимволы:
    - `%` - любое количество символов
    - `_` - один символ

```sql
WHERE test_name LIKE 'A%'
WHERE email LIKE '%@gmail.com'
WHERE code LIKE 'A_3'
```

### ILIKE
- Работает так же, как `LIKE`
- __Не чувствителен к регистру__ (PostgreSQL)

```sql
WHERE username ILIKE '%alex%'
```

### Escape последовательности в LIKE / ILIKE

Позволяют искать символы, которые обычно являются спецсимолами (`%` и `_`), экранируя их специальным символом.

```sql
WHERE столбец LIKE 'шаблон' ESCAPE 'символ'
WHERE pattern LIKE '100#% complete' ESCAPE '#'
```

# Оператор LIMIT

Ограничивает количество строк, возвращаемых запросом.

```sql
LIMIT количество OFFSET смещение

SELECT * FROM employees LIMIT 5;
SELECT * FROM orders LIMIT 10 OFFSET 20;
```

# Оператор ORDER BY

`ORDER BY` - оператор в SQL, который используется для сортировки результатов запроса. Позволяе упорядочить строки __по одному или нескольким столбцам__, в __возрастающем__ или __убывающем__ порядке.

```sql
SELECT столбцы
FROM таблица
ORDER BY столбец1 [ASC | DESC], столбец2 [ASC | DESC];
```

- `ASC` - сортировка по возрастанию (__по умолчанию__)
- `DESC` - сортировка по убыванию

# Оператор GROUP BY

`GROUP BY` - это оператор SQL, который объединяет строки с одинаковыми значениями в указанных столбцах в группы. Используется для получения __сводной информации__ по данным (анализ, отчеты, статистика).

```sql
SELECT колонка, агрегатная_функция (поле)
FROM таблица
GROUP BY колонка;
```

`GROUP BY` разбивает таблицу на отдельные __подтаблицы__, сгрупированные по какому-то полю.

Исходная таблица:

| id   | name   | faculty   |
|-     |-       |-          |
| 1    | Иван   | ФИ        |    
| 2    | Петр   | ФИ        |
| 3    | Катя   | ПММ       |

После `GROUP BY`:

| id   | name   | faculty   |
|-     |-       |-          |
| 1    | Иван   | ФИ        |    
| 2    | Петр   | ФИ        |

| id   | name   | faculty   |
|-     |-       |-          |
| 3    | Катя   | ПММ       |

## Агрегатные функции

- `COUNT()` - количество
- `SUM()` - сумма
- `AVG()` - среднее
- `MIN()`, `MAX()` - минимум / максимум

# Условия фильтрации с HAVING

- `HAVING` - оператор, который применяется для фильтрации резултатов после группировки.
- Испольузется вместе с `GROUP BY`.
- Позволяет фильтровать агрегированные значения (`SUM`, `COUNT`, `AVG` и другие).
- Похож на `WHERE`, но работает только после выполнения `GROUP BY`.

```sql
SELECT customer_id, SUM(amount) AS total
FROM payments
GROUP BY customer_id
HAVING SUM(amount) > 1000;
```

# Primary Key

`Первичный ключ` - это минимальный набор столбцов, однозначно идентифицирующий запись в таблице.

__Свойства PK__:
- Уникальность
- NOT NULL
- Неизменяемость (желательно на практике)
- Одно значение -> одна строка

__Примеры первичных ключей__:
- Идентификатор студента: **_student_id_**
- Номер заказа: **_order_id_**
- Составой ключ: (**_student_id_**, **_course_id_**)

```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,      -- первичный ключ
    full_name VARCHAR(100) NOT NULL,
    birthdate DATE 
);
```

# Foreign Key

`Внешний ключ` - столбец, который ссылается на первичный ключ другой таблицы.

__Ограничения внешних ключей__:
- `ON DELETE CASCADE` - удаление родителя -> удаление потомков
- `ON DELETE SET NULL` - родитель удален -> `FK` становится `NULL`
- `ON UPDATE CASCADE` - изменение `PK` -> обновление `FK`

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    student_id INT NOT NULL,
    order_date DATE NOT NULL DEFAULT CURRENT_DATE,
    FOREIGN KEY (student_id)
        REFERENCES students (student_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
```

# Проектирование схемы БД

## Этапы проектирования

1. Сбор требований
2. Определение сущностей
3. Определение атрибутов
4. Определение связей
5. Нормализация
6. Создание физической схемы

## Типовые связи

- Один-к-одному (`1:1`) - биография студента
- Один-ко-многим (`1:N`) - пользователь -> заказы
- Многие-ко-многим (`M:N`) - студенты <-> курсы (через таблицу связей)

Ограничение `UNIQUE` реализовывает связь `1:1`.

Для реализации `M:M` необходима развязочная таблица, __первичные ключи__ которой - это комбинации
__внешних ключей__.

## Нормальные формы

### 1NF - Первая нормальная форма

__Требования__:
- Отсутствие повторяющихся групп
- Каждое поле атомарно
- Есть первичный ключ

__До применения__ `1NF`:

| Фирма     | Модели        |
|-          |-              |
| Ferrari   | Enzo, F40     |    
| Lada      | Vesta, Granta |

__После применения__ `1NF`:

| Фирма     | Модели        |
|-          |-              |
| Ferrari   | Enzo          |    
| Ferrari   | F40           |
| Lada      | Vesta         |
| Lada      | Granta        |

### 2NF - Вторая нормальная форма

__Требования__:
- 1NF
- Нет частичных зависимостей от части составного ключа

__До применения__ `2NF`:

| Фирма     | Модели    | Цена      | Скидка    |
|-          |-          |-          |-          |
| Ferrari   | Enzo      | 1000000   | 0%        |
| Ferrari   | F40       | 5000000   | 0%        |
| Lada      | Vesta     | 15000     | 5%        |
| Lada      | Granta    | 10000     | 5%        |

__После применения__ `2NF`:


| Фирма     | Модели    | Цена      |
|-          |-          |-          |
| Ferrari   | Enzo      | 1000000   |
| Ferrari   | F40       | 5000000   |
| Lada      | Vesta     | 15000     |
| Lada      | Granta    | 10000     |

| Фирма     | Скидка    |
|-          |-          |
| Ferrari   | 0%        |
| Lada      | 5%        |

### 3NF - Третья нормальная форма

__Требования__:
- 2NF
- Отсутствие транзитивных зависимостей

__До применения__ `3NF`:

| Фирма     | Магазин       | Телефон   |
|-          |-              |-          |
| Ferrari   | Премиум АВТО  | 44-44-44  |
| Lada      | Бюджет АВТО   | 45-15-45  |

__После применения__ `3NF`:

| Фирма     | Магазин       |
|-          |-              |
| Ferrari   | Премиум АВТО  |
| Lada      | Бюджет АВТО   |

| Магазин       | Телефон   |
|-              |-          |
| Премиум АВТО  | 44-44-44  |
| Бюджет АВТО   | 45-15-45  |

# JOIN

Операции объединения строк двух таблиц на основе логического условия (обычно __по ключам__).

- `INNER JOIN` - Возвращает строки, где условие совпадения выполняется для обеих таблиц
- `LEFT JOIN` - Все строки из левой таблицы + совпавшие справа. Если совпадений нет - справа `NULL`
- `RIGHT JOIN` - Все строки из правой таблицы + совпавшие слева
- `FULL JOIN` - Все строки из обеих таблиц, совпавшие и не совпавшие. Отсутствующие значения заменяются `NULL`
- `CROSS JOIN` - Декартово произведение: каждая строка слева x каждая строка справа
- `SELF JOIN` - JOIN таблицы самой с собой

```sql
-- INNER JOIN
SELECT s.name, c.course_name
FROM students s
INNER JOIN enrollments e ON s.id = e.student_id
INNER JOIN courses c ON e.course_id = c.id;

-- LEFT JOIN
SELECT c.name, o.id, AS order_id
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id;
```

# Вложенный запрос

`Вложенный запрос` (`subquery`) - это запрос внутри другого SQL-запроса
- Используется как источник данных для внешнего запроса
- Выполняется сначала внутренний запрос, потом внешний

__Может использоваться в__:
- В предложении `WHERE`
- В предложении `FROM`
- В списке `SELECT`
- В инструкциях `INSERT`, `UPDATE`, `DELETE`

```sql
SELECT test_name
FROM employees
WHERE dept_id = (
    SELECT id FROM departments WHERE test_name = 'Sales'
);
```

## Типы вложенных запросов

- `Скалярные` (`Scalar subqueries`) - возвращают одно значение
- `Строковые` (`Row subqueries`) - возвращают одну строку
- `Табличные` (`Table subqueries`) - возвращают таблицу
- `Коррелированные` (`Correlated subqueries`) - используют данные внешнего запроса

### Скалярный подзапрос

- Возвращает одно значение
- Можно использовать как константу

```sql
SELECT test_name, salary,
    (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;
```

### Подзапросы с IN / ANY / ALL

- `IN` - соответствует любому значению из списка
- `ANY` - хотя бы одно значение удовлетворяет условию
- `ALL` - все значения удовлетворяют условию

```sql
SELECT test_name
FROM employees
WHERE dept_id IN (  -- соответствует любому значению из списка
    SELECT id FROM departments WHERE region = 'EU'
);
```

### Подзапросы в FROM (табличные подзапросы)

- Выполняется для каждой строки внешнего запроса
- Ссылается на поля внешней таблицы

```sql
SELECT dept_name, avg_salary
FROM (
    SELECT dept_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY dept_id
) t
JOIN departments d ON d.id = t.dept_id;
```

### Коррелированный подзапрос

- Выполняется для каждой строки внешнего запроса
- Ссылается на поля внешней таблицы

```sql
SELECT e.test_name
FROM employees e
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE dept_id = e.dept_id
);
```

# CTE

`CTE` - временный набор данных, определенный перед основным запросом.

- Создается с помощью ключевого слова `WITH`
- Можно рассматривать как "временную таблицу", существующую только в рамках одного запроса

```sql
WITH cte_name AS (
    SELECT ...
)
SELECT ...
FROM cte_name;
```

```sql
WITH high_salary AS (
    SELECT test_name, salary
    FROM employees
    WHERE salary > 100000
)
SELECT test_name
FROM high_salary
ORDER BY test_name;
```

# Оператор CASE

Оператор `CASE` позволяет выполнить условные проверки внутри SQL.
- Работает аналогично __условному оператору__.
- Возвращает значение в зависимости от условий.

__Где используется__ `CASE`:
- В блоке `SELECT`
- В условиях `WHERE`
- В выражениях `ORDER BY`
- При формировании вычисляемых полей

```sql
CASE
    WHEN условие THEN результат
    [WHEN условие THEN результат ...]
    [ELSE результат]
END
```

```sql
    SELECT test_name, salary
        CASE
            WHEN salary > 100000 THEN 'High'
            WHEN salary > 50000 THEN 'Medium'
            ELSE 'Low'
        END AS salary_level
    FROM employees;
```

# Изменение таблиц и удаление данных

## Команда ALTER TABLE

`ALTER TABLE` - команда SQL, предназначенная для изменения структуры уже существующей таблицы без удаления данных.

__Используется для__:
- добавления и удаления столбцов
- изменения типов данных
- добавления и удаления ограничений
- переименования таблиц и столбцов

```sql
ALTER TABLE имя_таблицы
    действие;
```

### Добавление столбца

```sql
ALTER TABLE users
ADD COLUMN age INTEGER;
```

### Добавление столбца с указанием значения по умолчанию

```sql
ALTER TABLE users
ADD COLUMN created_at TIMESTAMP DEFAULT now();
```

### Удаление столбца

```sql
ALTER TABLE users
DROP COLUMN age;
```

### Изменение типа столбца явно

```sql
ALTER TABLE users
ALTER COLUMN surname TYPE INT
USING surname::integer;
```
### Обновление данных в существующей таблице

```sql
UPDATE users
SET surname = 13
WHERE id = 1
```

### Переименование таблицы

```sql
ALTER TABLE users
RENAME TO accounts;
```
### Переименование столбца

```sql
ALTER TABLE users
RENAME COLUMN test_name TO full_name;
```

## Команда DELETE

`DELETE` - команда для удаления строк из таблицы.

__Может__:
- удалять отдельные строки
- удалять группы строк
- очищать всю таблицу

```sql
DELETE FROM имя_таблицы
WHERE условие;
```

__Удаление всех строк__:

```sql
DELETE FROM users;

TRUNCATE TABLE users;
```

`TRUNCATE` работает быстрее, чем `DELETE`, и выполняется __вне транзакций__ (но в Postgres можно
откатить). Нельзя использовать __условия__ и __триггеры__.

# EXPLAIN и EXPLAIN ANALYZE

Инструменты для анализа выполнения запросов.

- `EXPLAIN` - показывает план выполнения
- `EXPLAIN ANALYZE` - выполняет запрос и показывает реальные метрики

Ключевые элементы плана:
- Seq Scan / Index Scan
- Nested Loop / Hash Join / Merge Join
- Cost, Rows, Actual Time

# Индексы

`Индекс` - это вспомогательная структура данных, ускоряющая поиск строк в таблице.

Аналогия:
- `Таблица` - это книга
- `Индекс` - это алфавитный указатель

Без индекса __PostgreSQL__ выполняет `последовательное сканирование` (`Seq Scan`) всей таблицы.

## Зачем нужны индексы?

Индексы позволяют:
- Ускорять `SELECT`
- Оптимизировать `WHERE`, `JOIN`, `ORDER BY`, `GROUP BY`
- Уменьшать нагрузку на диск и CPU

Цена индексов:
- Замедление `INSERT` `UPDATE`, `DELETE`
- Дополнительное место на диске

## Когда индексы НЕ нужны?

- Таблица __маленькая__
- Колонка имеет __низкую селективность__
- Запросы __редко выполняются__
- Данные __часто обновляются__

## Основные типы индексов в PostgreSQL

PostgreSQL поддерживает несколько типов индексов:
- `B-tree` (по умолчанию)
- `Hash`
- `GIN`
- `GiST`
- `SP-GiST`
- `BRIN`

Каждый тип решает свою задачу

### B-tree индекс

Структура:

```
        ---------
        |1|7|...|
        ---------
        /       \
    -----       ----------
    |1|4| ----- |7|10|...|
    -----       ----------
    /    \               \
-------    -------    -------
|1|2|3| -- |4|5|6| -- |7|8|9|
-------    -------    -------
```

Подходит для операций:
- `=`
- `<`, `>`, `<=`, `>=`
- `BETWEEN`
- `ORDER BY`

Используется для:
- Первичных ключей
- Уникальных ограничений

```sql
CREATE INDEX index_name
ON table_name USING BTREE (column_name1, column_name2, ...);
```

__Профилирование запроса__

```sql
INSERT INTO users (email)
SELECT
    'user' || gs || '@example.com'  -- конкатенация строки (например, user1@example.com)
FROM generate_series(1, 1000000) AS gs;

EXPLAIN SELECT id, email FROM users         -- EXPLAIN покажет план выполнения
WHERE email = 'user777555@example.com'

EXPLAIN ANALYZE SELECT id, email FROM users -- EXPLAIN ANALYZE реально выполнит запрос
WHERE email = 'user777555@example.com'
```
Query Plan:

|                       | Без B-tree    | B-tree    |
| -                     |-              |-          |
| Planning Time (ms)    | 0.048         | 0.316     |
| Execution Time        | 23.218        | 0.122     |

Кейс с полным перебором страницы (долгий поиск):

```sql
EXPLAIN ANALYZE SELECT id, email FROM users
WHERE LOWER(email) = 'user777555@example.com'
```

Решение - `функциональный индекс`:

```sql
CREATE INDEX users_email_lower_idx
ON users (LOWER(email))
```

В __highload__ используют отдельную БД для чтения с индексами, и отдельную для записи, которые
консистенты, но с задержкой. (`CQRS`)

### Hash индекс

Особенности:
- Работает только с оператором `=`
- Быстр в точечных запросах

Ограничения:
- Не поддерживает сортировку
- Используется реже `B-tree`

```sql
CREATE INDEX idx_table_cols_hash
ON table_name USING HASH(column1, column2, ...);
```

### GIN индекс

Подходит для сложных структур:
- `ARRAY`
- `JSONB`
- `tsvector` (полнотекстовый поиск)

Примеры задач:
- Поиск элементов в массиве
- Поиск по JSON-полям
- Full-text search

```sql
CREATE INDEX index_name
ON table_name
USING GIN(column_name);
```

# Представления VIEW

`VIEW` - это сохраненный SQL-запрос, который ведет себя как виртуальная таблица.

Ключевые особенности:
- Не хранит данные физически
- Каждый запрос к `VIEW` пересчитывается заново
- Всегда возвращает актуальные данные
- Упрощает сложные SQL-запросы

```sql
CREATE VIEW active_users AS
SELECT id, name, email,
FROM users
WHERE is_active = true
```

Обращение к `VIEW`:

```sql
SELECT *
FROM active_users;
```

## Materialized VIEW

`MATERIALIZED VIEW` - это представление, которое физически __хранит результат запроса__.

Ключевые особенности:
- Данные сохраняются на диске
- Запросы выполняются значительно быстрее
- Данные могут быть устаревшими
- Требует ручного обновления

```sql
CREATE MATERIALIZED VIEW sales_summary AS
SELECT
    product_id,
    SUM(amount) AS total_sales
FROM sales
GROUP BY product_id;
```

Ручное обновление данных:

```sql
REFRESH MATERIALIZED VIEW sales_summary;
```

# Сложные типы данных

## JSON / JSONB

`JSON` и `JSONB` используются для хранения полуструктурированных данных.

Преимущества `JSONB`:
- Быстрый доступ к элементам
- Поддержка `GIN` индексов
- Удобен для динамических схем данных

Пример `JSON`:

```sql
INSERT INTO profiles (data)
VALUES (
    '{
        "name": "Анна",
        "age": 30,
        "skills": ["SQL", "Python"]
    }'
);
```

Пример `SELECT`:

```sql
SELECT data->'skills' FROM profiles;    -- ["SQL", "Python"]
```

Получение `JSON`:

```
->
```

Получение текста:

```
->>
```

Взятие 0-го элемента из массива `JSON`:

```sql
SELECT data->'skills'->>0 FROM profiles;
```

Запрос для `JSONB`:

```sql
SELECT * FROM profiles_b
WHERE data->>'name' - 'Анна';
```

Поиск по наличию ключа:

```sql
SELECT * FROM profiles_b
WHERE data ? 'skills';
```

Запрос по включению:

```sql
SELECT * FROM profiles_b
WHERE data @> '{"age": 30}';
```

Поиск по наличию поля в массиве `JSON`:

```sql
SELECT * FROM profiles_b
WHERE data->'skills' ? 'SQL';
```

Обновление значения:

```sql
UPDATE profiles_b
SET data = jsonb_set(data, '{age}', '31')
WHERE id = 1;
```

## ARRAY

Массивы позволяют хранить наборы значений __одного типа__ в __одном поле__.

Особенности:
- Поддержка одномерных и многомерных массивов
- Возможность поиска по элементам
- Индексация через `GIN`

Индексация массива начинается с `1`.

Пример массива:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name TEXT,
    phones TEXT[]
);
```

Добавление элементов:

```sql
INSERT INTO students (name, phones)
VALUES
('Анна', ARRAY['+712', '+713']),
('Иван', ARRAY['+719']),
```

Выборка определенного элемента массива:

```sql
SELECT name, phones[1] FROM students
```

Проверка на наличие:

```sql
SELECT name FROM students
WHERE '+713' = ANY(phones)
```

Проверка на включение:

```sql
SELECT name FROM students
WHERE phones @> ARRAY['713']
```

# Расширения PostgreSQL

`Расширения PostgreSQL` - это подключаемые модули, которые добавляют в базу данных __новый функционал__ без изменения ядра СУБД.

Они могут расширять __PostgreSQL__:
- новыми типами данных
- функциями и операторами
- индексами и методами доступа
- языками процедур (`PL`)

__Ключевые особенности расширений__:
- Устанавливаются командой `CREATE EXTENSION`
- Управляются на уровне базы данных
- Безопасны для обновлений __PostgreSQL__
- Поставляются как с __PostgreSQL__, так и сторонними разработчиками

Вывод расширений, которые доступны в __PostgreSQL__:

```sql
SELECT name, default_version, installed_version, comment
FROM pg_available_extensions
ORDER BY name
```

Вывод установленных расширений:

```sql
SELECT extname, extversion
FROM pg_extension
```

Подключение расширения:

```sql
CREATE EXTENSION pg_trgm;
```

## PostGIS

Расширение для работы с географическими и геометрическими данными.

Возможности:
- Хранение координат и геометрий
- Пространственные индексы (GiST)
- Гео-запросы: расстояния, пересечения, зоны

Применение:
- карты
- логистика
- геоаналитика

## pg_trgm

Расширение для триграммного поиска строк.

Возможности:
- Поиск по частичному совпадению
- Быстрый `LIKE` и `ILIKE`
- Поиск с опечатками

Используется для:
- полнотекстового поиска
- автодополнения
- `fuzzy search`

Проверка на наличие расширения:

```sql
SELECT * FROM pg_available_extensions WHERE name = 'pg_trgm'
```

Мера похожести строк (`Similarity`):

```sql
SELECT similarity('postgres', 'postgress')
```

|   | similarity    |
|-  | -             |
| 1 | 0.72727275    |

```sql
SELECT 'postgres' % 'postgress'
```

|   | ?column? boolean  |
|-  | -                 |
| 1 | true              |

Порог похожести (`0.3` по умолчанию)

```sql
SHOW pg_trgm_similarity_threshold;
```

|   | pg_trgm_similarity_threshold text     |
|-  | -                                     |
| 1 | 0.3                                   |

```sql
SET pg_trgm_similarity_threshold = 0.4
```

Полнотекстовый поиск:

```sql
SELECT name, similarity(name, 'iphon') AS sim
FROM products
WHERE % name 'iphon'
ORDER BY sim DESC
```
|   | name text | sim real      |
|-  |-          |-              |
| 1 | IPhone 13 | 0.45454547    |
| 2 | IPhone 14 | 0.45454547    |

# Основные параметры конфигурации PostgreSQL

Основные параметры конфигурации:
- `shared_buffers` - память под кеш данных
- `work_mem` - память на сортировки и `JOIN`
- `maintenance_work_mem` - операции `VACUUM` / `CREATE INDEX`
- `effective_cache_size` - оценка кеша ОС

Пример изменения:

```sql
ALTER SYSTEM SET work_mem = '32MB'
ALTER SYSTEM SET effective_cache_size = '24GB'
```

# Транзакции, блокировки и параллелизм в PostgreSQL

## Зачем нужны транзакции

`Транзакция` - логическая единица работы с БД, которая:
- либо выполняется полностью
- либо не выполняется вовсе

__Проблема__:
- __Несколько пользователей__ работают с БД одновременно
- Изменения могут __конфликтовать__
- Возможны __потеря данных__ и __неконсистентные состояния__  

## ACID - фундамент транзакций

`ACID` - набор свойств корректной транзакции:
- `A` - `Atomicity` (`Атомарность`)
  Транзакция выполняется целиком или откатывается полностью
- `C` - `Consistency` (`Согласованность`)
  БД переходит из одного корректного состояния в другое
- `I` - `Isolation` (`Изоляция`)
  Параллельные транзакции не мешают друг другу
- `D` - `Durability` (`Долговечность`)
  Зафиксированные данные не теряются при сбоях

## BEGIN / COMMIT / ROLLBACK

Базовый жизненный цикл транзакции:

```sql
BEGIN;

UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;

COMMIT;
```

- `BEGIN` - начало транзакции
- `COMMIT` - зафиксировать изменения
- `ROLLBACK` - откатить изменения

## Уровни изоляции транзакций

SQL-стандарт определяет 4 уровня изоляции:
- `Read Uncommitted` (невозможен в `PostgreSQL`)
- `Read Committed` (по умолчанию в `PostgreSQL`)
- `Repeatable Read`
- `Serializable`

### Read Committed

В рамках первой транзакции получили новые данные после __подтверждения второй транзакции__. 

Сессия 1:

```sql
BEGIN;

SELECT name FROM students WHERE id = 1;
```

| name  |
| -     |
| Стив  |

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = 'Новый Стив' WHERE id = 1;

COMMIT;
```

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1;

COMMIT;
```

| name        |
| -           |
| Новый Стив  |

### Repeatable Read

Первая транзакция видит __один и тот же__ снапшот данных со старым значением. Чтение всегда __повторное__, даже если данные __изменены__ второй транзакцией.

Сессия 1:

```sql
BEGIN ISOLATION LEVEL REPEATABLE READ;

SELECT name FROM students WHERE id = 1;
```

| name        |
| -           |
| Новый Стив  |

Сессия 2:

```sql
BEGIN; 

UPDATE students SET name = 'Стив' WHERE id = 1;

COMMIT;
```

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1;

COMMIT;
```

| name        |
| -           |
| Новый Стив  |

Сессия 2:

```sql
SELECT name FROM students WHERE id = 1;
```

| name        |
| -           |
| Стив        |

### Serializable

Полностью блокирует таблицу. `PostgreSQL` отменяет одну из транзакций, чтобы сохранить иллюзию последовательного выполнения. Необходимо начинать транзакцию __заново уже с обновленными данными__.

Сессия 1:

```sql
BEGIN ISOLATION LEVEL SERIALIZABLE;

SELECT name FROM students WHERE id = 1;
```

| name        |
| -           |
| Стив        |

Сессия 2:

```sql
BEGIN ISOLATION LEVEL SERIALIZABLE;

UPDATE students SET name = 'Елена' WHERE id = 1;

COMMIT;
```

Сессия 1:

```sql
UPDATE students SET name = 'Григорий' WHERE id = 1;
```

```
ERROR: could not serialize access due to concurrent update 
```

```sql
ROLLBACK;
```

## MVCC - Multi-Version Concurrency Control

Идея `MVCC`:
- При изменении строки создается __новая версия__
- Старые версии остаются доступными другим транзакциям
- Чтение не блокирует запись и наоборот

Преимущества:
- высокая параллельность
- меньше блокировок
- масштабируемость

## Как PostgreSQL видит данные?

Каждая транзакция:
- имеет свой __snapshot__
- видит только __зафиксированные версии__, актуальные на момент старта

Поэтому:
- нет dirty read
- чтения почти не блокируются

При `Read Committed` снапшот создается на каждый `SELECT`, поэтому можно увидеть новые данные после `COMMIT` другой транзакции.

При `Repeatable Read` снапшот создается один раз в начале транзакции, поэтому все `SELECT` видят одинаковые данные.

При `Serializable` то же самое, что и `Repeatable Read`, но также контроль чтения и записи.

`VACUUM` - операция в рамках `PostgreSQL`, которая является уборщиком `MVCC` и удаляет снапшоты.

Когда работает `VACUUM`, он блокирует таблицу на запись и изменения. 

## Блокировки в PostgreSQL

Несмотря на `MVCC`, блокировки все равно существуют:
- для изменения данных
- для защиты схемы
- для сериализации операций

### Типы блокировок

По уровню:
- `Row-level` - блокировка строк
- `Table-level` - блокировка таблиц

По режиму:
- `Shared (S)` - совместное чтение
- `Exclusive (X)` - эксклюзивная запись

#### Row-level блокировки

Используются при:
- `UPDATE`
- `DELETE`
- `SELECT FOR UPDATE`

Сессия 1:

```sql
BEGIN;

UPDATE students SET name = 'Новое имя' WHERE id = 1;
```

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = 'Имя 2' WHERE id = 1;
-- Сессия 2 заблокировалась и ждет завершения сессии 1
```

Сессия 1:

```sql
COMMIT;
-- Теперь сессия 2 разблокирована

SELECT name FROM students WHERE id = 1;
```

| name      |
| -         |
| Новое имя |

Сессия 2:

```sql
COMMIT;
```

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1;
```

| name      |
| -         |
| Имя 2     |

#### Table-level блокировки

Используются при:
- `LOCK TABLE`
- DDL-операциях (`ALTER TABLE`, `DROP`)

```sql
LOCK TABLE accounts IN EXCLUSIVE MODE;
```

Сессия 1:

```sql
BEGIN;

LOCK TABLE students IN ACCESS EXCLUSIVE MODE;
-- Блокирует таблицу
```

Сессия 2:

```sql
SELECT * FROM students
-- Сессия 2 заблокирована и ждет завершения (COMMIT) сессии 1
```

### Deadlock (Взаимная блокировка)

Сессия 1:

```sql
BEGIN;

UPDATE students SET name = 'Имя 12' WHERE id = 1; 
```

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = 'Имя 22' WHERE id = 2; 
```

Сессия 1:

```sql
BEGIN;

UPDATE students SET name = 'Имя 32' WHERE id = 2; 
```

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = 'Имя 42' WHERE id = 1; 
```

```
ERROR: deadlock detected
```

`PostgreSQL` убил вторую сессию после обнаружения дедлока.

### Просмотр блокировок

```sql
SELECT locktype, mode, relation::regclass FROM pg_locks; 
```

| locktype      | mode                | relation  |
| -             | -                   | -         |
|virtualxid     | ExclusiveLock       |           |
| relation      | AccessShareLock     | pg_locks  |
| virtualxid    | ExclusiveLock       |           |
| relation      | AccessExclusiveLock | students  |
| transactionid | ExclusiveLock       |           |

### SELECT FOR UPDATE

Назначение:
- защитить строки от изменений другими транзакциями

Типичный кейс:
- банковские операции
- очереди
- бронирование ресурсов

```sql
BEGIN;

SELECT * FROM tickets WHERE id = 10 FOR UPDATE;
UPDATE tickets SET status = 'sold' WHERE id = 10;

COMMIT;
```

__Кейс__

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1;
```

| name    |
| -       |
| Имя 12  |

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = '424242' WHERE id = 1;

COMMIT;
```

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1;
-- Данные были изменены сессией 2
COMMIT;
```

| name    |
| -       |
| 424242  |

__Решение__

Сессия 1:

```sql
SELECT name FROM students WHERE id = 1 FOR UPDATE;
```

| name    |
| -       |
| Имя 12  |

Сессия 2:

```sql
BEGIN;

UPDATE students SET name = '424242' WHERE id = 1;
-- Сессия 2 заблокирована из-за FOR UPDATE
```

# Совместный доступ: пессимистическая и оптимистическая модели

## Оптимистическая модель

`Оптимистическая модель` - сначала работа, затем проверка. 

Проверка конфликтов происходит при коммитев в случае когда конфликты редкие. За контролем версий должно следить ПО при помощи `concurrency stamp` в виде поля `version` таблицы, либо по временной отметке `updated_at`.

## Пессимистическая модель

`Пессимистическая модель` - сначала блокировка, затем работа.
попадания 
Конфликты частые и долгие.

Параметры `FOR UPDATE`:
- `NOWAIT` - если строка уже заблокирована, то транзацкия не будет заблокирована, сразу ошибка. 
- `SKIP LOCKED` - транзакция пропускает заблокированные строки.

# Курсоры

`Курсор` - указатель на набор строк результата, который позволяет получать строки порциями и интервально обрабатывать результат без передачи всего результата сразу.

Необходим для обработки большой выборки (`batch processing`).

В рамках `PostgreSQL` курсор живет внутри транзакции и использует снапшот этой транзакции.

```sql
BEGIN;

DECLARE c CURSOR FOR
  SELECT id, owner, balance FROM account;
```

```sql
-- в рамках транзакции
FETCH 1 FROM c;
```

|id|owner|balance|
|-|-|-|
|1|alice|80.00|

```sql
-- в рамках транзакции
FETCH NEXT FROM c;
```

|id|owner|balance|
|-|-|-|
|2|bob|60.00|

# Введение в NoSQL

## CAP-теорема

`CAP-теорема` гласит, что есть 3 свойства распределенных систем:
- `Consistency` - все узлы видят одно и то же состояние сразу после записи.
- `Availability` - система отвечает на запросы после записи (необязательно правильно)
- `Partition tolerance` - система продолжает работать даже если сеть разделена на части, которые не могут общаться друг с другом.

NoSQL системы часто проектируются вокруг принципа `eventual consistency`.

Выделяют семейства NoSQL систем:
- `Key-value`
- `Document`
- `Column`
- `Graph`
- `TMSDB`

# Redis

## Запуск

Запуск `Redis` в docker-контейнере:

```bash
docker run -d --name redis-dev -p 6379:6379 redis:7
```

Просмотр логов:

```bash
docker logs redis-dev --tail 20
```

Установка `redis-tools`:

```bash
sudo apt install -y redis-tools
```

Подключение к `redis`:

```bash
redis-cli -h 127.0.0.1 -p 6379
```

По умолчанию на `redis` не установлен пароль.

## Команды

Проверка доступности `redis`:

```bash
PING
```

Запись значения:

```bash
SET user:42:name "Alice"
```

```bash
SET name "Oleg"
```

`user:42:name` и `name` являются __ключами__. Двоеточия создают подобие вложенности и структуры ключей.

Получение значения по ключу:

```bash
GET name
```

Проверка существования ключа:

```bash
EXISTS name
```

Работа с счетчиком:

```bash
SET page:main:views 0
```

Инкрементация счетчика:

```bash
INCR page:main:views
```

Явное увеличение:

```bash
INCRBY page:main:views 10
```

Установка времени жизни:

```bash
SET token "abc" EX 10
```

Вывод TTL:

```bash
TTL token
```

Типы данных в Redis:
- Hash
- List
- Set
- Sorted Set

```bash
HSET user profile:name "Oleg" profile:city "Moscow"
```

```bash
HGET user profile:name
```

```bash
HGETALL user
```

LIST

```bash
LPUSH q:tasks "t1" "t2" "t3"
```

```bash
LRANGE q:tasks 0 -1
```

```bash
RPOP q:tasks
```

SET

```bash
SADD tags "db" "redis" "backend" "redis"
```

```bash
SMEMBERS tags
```

```bash
SISMEMBER tags "redis"
```

```bash
SREM tags "123"
```

Sorted Set

```bash
ZADD leader 100 "alice" 250 "bob" 30 "oleg"
```

```bash
ZREVRANGE leader 0 2 WITHSCORES
```

```bash
ZINCRBY leader 50 "alice"
```

Просмотреть все существующие ключи (блокирует базу, пока сканирует ключи, в продакшене не рекомендуется использовать):

```bash
KEYS *
```

```bash
SCAN 0 MATCH * COUNT 3
```

```bash
SCAN 0 MATCH user* COUNT 3
```

Конфигурация Redis

