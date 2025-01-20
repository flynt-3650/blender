# Темы вопросов к экзамену 5 семестра по дисциплине «Разработка баз данных»

## 1. Нормализация. Определения, алгоритм

**Нормализация** - процесс приведения структуры базы данных к виду, минимизирующему избыточность данных и зависимость между ними. Цель - улучшить структуру таблиц и уменьшить риски аномалий вставки, обновления и удаления.

**Определения:**

- **Функциональная зависимость:** отношение между атрибутами таблицы, при котором значение одного атрибута однозначно определяет значение другого (X -> Y).
- **Транзитивная зависимость:** зависимость вида X -> Z, если существует X -> Y и Y -> Z, где X - первичный ключ.
- **Аномалии:** проблемы, возникающие при работе с таблицами, не прошедшими нормализацию (вставка, удаление, обновление).

**Алгоритм нормализации:**

1. **Первая нормальная форма (1NF):**
   - Удалить повторяющиеся группы данных.
   - Все значения атрибутов должны быть атомарными (неразделимыми).

2. **Вторая нормальная форма (2NF):**
   - Удалить частичные функциональные зависимости.
   - Каждое неключевое поле должно зависеть от всего составного первичного ключа, если он есть.

3. **Третья нормальная форма (3NF):**
   - Удалить транзитивные зависимости.
   - Неключевые атрибуты должны зависеть только от первичного ключа, а не от других неключевых атрибутов.

4. **Бойс-Кодд нормальная форма (BCNF):**
   - Для каждой функциональной зависимости X -> Y, X должен быть суперключом.

5. **Четвёртая нормальная форма (4NF):**
   - Удалить многозначные зависимости.
   - Записи должны зависеть только от ключа, а не от нескольких независимых атрибутов.

6. **Пятая нормальная форма (5NF):**
   - Устранить соединительные зависимости.
   - Декомпозиция таблиц должна быть полной и корректной.

---

## 2. Диаграммы "сущность-связь". Уровни, методы, средства, ограничения

**ER-диаграммы** используются для моделирования данных, определяя сущности, их атрибуты и связи.

**Уровни:**

1. **Концептуальный уровень**: показывает основные сущности и связи между ними, без технических деталей.
2. **Логический уровень**: добавляет атрибуты и типы данных, но не привязан к конкретной СУБД.
3. **Физический уровень**: включает детали реализации (типы столбцов, индексы, ограничения).

**Методы:**

1. **Сущности:** прямоугольники, обозначаюзие объекты системы.
2. **Связи:** ромбы или линии, описывающие взаимосвязи сущностей.
3. **Атрибуты:** овалы или текст рядом с сущностью, указывающие характеристики.

**Средства:**

- Ручной подход.
- Автоматические средства (DB Designer, MySQL Workbench, ER/Studio, Lucidchart).

**Ограничения:**

- Кардинальность - указывает минимальное и максимальное число сущностей, связанных между собой (1:1, 1:N, N:M).
- Тип связи - обязательная (обозначается двойной линией) или необязательная (одинарная линия).
- Первичный ключ - атрибут, уникально идентифицирующий сущность.
- Внешний ключ - обеспечивает целостность связи между сущностями.

## 3. Структура языка SQL. DDL, DML, DQL, Средства управления транзакциями, Средства администрирования данных

**Структура языка SQL:**

1. **DDL**: используется для создания, изменения и удаления структуры БД.
    - `CREATE`: создание объектов (таблиц, индексов и т.д.).
    - `ALTER`: изменение существующих объектов.
    - `DROP`: удаление объектов.
2. **DML**: Для вставки, обновления, удаления данных.
    - `INSERT`: добавление данных в таблицу.
    - `UPDATE`: обновление данных.
    - `DELETE`: удаление данных.
3. **DQL**: Для выборки данных из базы.
    - `SELECT`: запрос данных.
4. **Средства управления транзакциями**: позваоляют управлять несколькими операциями, как единым целым.
    - `BEGIN`: начало транзакции.
    - `COMMIT`: подтверждение изменений.
    - `ROLLBACK`: откат изменений.
5. **Средства администрирования данных**: Для управления пользователями, правами и доступом.
    - `GRANT`: предоставление прав.
    - `REVOKE`: отзыв прав.
    - `CREATE USER` / `DROP USER` - управление пользователями.

## 4. Типы данных языка SQL. Категории, группы

1. **Числовые данные**:
    - `TINYINT`: от -128 до 127 или 0-255 если `UNSIGNED`.
    - `SMALLINT`: от -32768 до 32767.
    - `MEDIUMINT`: от -8388608 до 8388607.
    - `INT/INTEGER`: от -2147483648 до 2147483647.
    - `BIGINT`: от -9223372036854775808 до 9223372036854775807.
    - `FLOAT`: числа с плавающей точкой.
    - `DOUBLE`: числа с плавающей точкой двойной точности.
    - `DECIMAL/NUMERIC` - точные числа с фиксированной точкой.
2. **Символьные данные**:
    - `CHAR(n)`: строка фиксированной длины n (до 255 символов).
    - `VARCHAR(n)` - строка переменной длины до n (макс. 65535 символов).
    - `TEXT` - большие текстовые блоки.
    - `BINARY` - фиксированная длина бинарных данных.
    - `VARBINARY` - переменная длина бинарных данных.
3. **Дата и время**:
    - `DATE`: дата (формат YYYY-MM-DD).
    - `TIME`: время (формат HH:MM:SS).
    - `DATETIME`: дата и время (формат YYYY-MM-DD HH:MM:SS).
    - `TIMESTAMP`: дата и время с зоной UTC.
    - `YEAR`: год (формат YYYY).
4. **Логические данные**:
    - `BOOLEAN`: логический.
5. Пространственные данные:
    - `GEOMETRY`: общий тип для геометрических данных.
    - `POINT`: точка.
    - `LINESTRING`: линии.
    - `POLYGON`: полигоны.

## 5. SQL – операторы. Структура, нотации, форматы конструкций

**SQL-операторы** - это команды для выполнения различных операций с БД.

1. **Структура SQL-оператора:**
    - **Основные команды SQL**: `SELECT`, `INSERT`, `UPDATE` и т.д.
    - **Идентификаторы**: названия таблиц, столбцов, индексов и т.д.
    - **Выражения**: Операции и значения, с которыми работают операторы.
    - **Условия**: Фильтры для выбора данных (`WHERE`, `HAVING`).
    - **Сортировка и группировка**: Упорядочивание и объединение данных (`ORDER BY`, `GROUP BY`).

    **Пример:**

    ```sql
    SELECT columns 
    FROM table_name 
    WHERE condition 
    GROUP BY column 
    HAVING condition 
    ORDER BY column ASC|DESC 
    LIMIT n OFFSET m;
    ```

2. **Нотации:**
    - **Строгая последовательность**: Команды должны следовать определённому порядку (например, в `SELECT` - `FROM` идёт после списка столбцов, а `WHERE` перед `ORDER BY`).
    - **Заглавные буквы для ключевых слов**: Обычно ключевые слова пишутся в верхнем регистре для удобства чтения.
    - **Чувствительность к пробелам**: SQL не чувствителен к пробелам, но важно их использовать для читаемости.

## 6. Основные объекты языка SQL

1. **Tables**: хранят структурированные данные в виде строк и столбцов.
2. **Columns**: определяют тип данных, который будет храниться в таблице.
3. **Indexes**: ускоряют поиск данных.
4. **Constraints**: правила для данных в таблице. (PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE).
5. **Views**: виртуальные таблицы, основанные на результатах запросов.
6. **Stored Procedures**: наборы SQL-команд для выполнения сложных операций.
7. **Functions**: возвращают значение на основе входных данных.
8. **Triggers**: автоматически выполняют команды при изменении данных.
9. **Sequences**: генерируют последовательные значения.
10. **Schemas**: логическая группа объектов в БД.
11. **Users, Roles**: определяют права доступа.

## 7. Индексы

**Индекс** - структура, которая ускоряет выполнение запросов в БД, обеспечивая быстрый доступ к данным в таблице.

**Виды индексов**:

1. **Standard** - ускоряют поиск.
2. **Unique** - гарантируют уникальность значений в столбце.
3. **Primary Key** - создаётся автоматически при определении первичного ключа.
4. **Composite** - включают несколько столбцов.

**Преимущества:**

- Ускорение поиска и фильтрации.
- `JOIN`, `ORDER BY` и `GROUP BY` выполняются быстрее.
**Недостатки:**
- Замедление операций вставки, обновления и удаления.
- Занимают дополнительное место.

## 8. Правила и стратегии поддержания целостности данных

**Целостность данных** - это соблюдение согласованности, точности и корректности данных в БД.

**Правила целостности:**

1. **Сущностная целостность:** в каждой таблице должен быть PK.
2. **Ссылочная целостность:** FK должен ссылаться на существующую запись в связанной таблице.
3. **Доменная целостность:** данные в столбцах должны соответствовать указанным типам и ограничениям.
4. **Бизнес-целостность:** логика должна соответсвовать бизнес-правилам.

**Стратегии поддержания целостности:**

1. Ограничения на уровне СУБД.
2. **Триггеры:** автоматические проверки и действия при изменении данных.
3. **Процедуры:** контроль сложной логики перед изменением данных.
4. **Транзакции.
5. Валидация через скрипты, отчёты и мониторинг.

## 9. Извлечение данных с использование языка SQL

**Извлечение данных в SQL** выполняется с помощью команды `SELECT`.

**Ключевые элементы:**

1. **Выбор столбцов**:
    - **Все столбцы:** `SELECT * FROM table_name;`
    - **Определённые столбцы:** `SELECT column1, column2 FROM table_name;`
2. **Фильтрация данных:** `SELECT column FROM table_name WHERE condition;`
3. **Сортировка:** `SELECT column FROM table_name ORDER BY column ASC;`
4. **Группировка:** `SELECT column, COUNT(*) FROM table_name GROUP BY column;`
5. **Фильтрация групп:** `SELECT column, COUNT(*) FROM table_name GROUP BY column HAVING COUNT(*) > 1;`
6. **Ограничение результата:** `SELECT column FROM table_name LIMIT 10 OFFSET 5;`
7. **Объединение таблиц:** `SELECT a.column, b.column FROM table1 a JOIN table2 b ON a.id = b.id;`
8. **Подзапросы:** `SELECT column FROM table_name WHERE id IN (SELECT id FROM other_table);`

## 10. Обобщение данных с помощью агрегатных функций

**Агрегатные функции** упрощают анализ данных, позволяя вычислять ключевые показатели..

**Агрегатные функции:**

1. `COUNT()`: Возвращает количество строк.
2. `SUM()`: Суммирует значения в столбце.
3. `AVG()`: Вычисляет среднее значение.
4. `MIN()`: Находит минимальное значение.
5. `MAX()`: Находит максимальное значение.

Агрегатные функции можно использовать вместе с **GROUP BY**. Для фильтрации групповых данных используется **HAVING**.

## 11. Многотабличные запросы, подзапросы

**Многотабличные запросы** используются для получения данных из нескольких таблиц с помощью соединений.

**Типы `JOIN`:**

1. `INNER JOIN`: возвращает строки, у которых есть совпадения в обеих таблицах.
2. `LEFT JOIN`: возвращает все строки из левой таблицы и совпадающие строки из правой.
3. `RIGHT JOIN`: возвращает все строки из правой таблицы и совпадающие строки из левой.
4. `FULL OUTER JOIN`: возвращает все строки из обеих таблиц (если поддерживается СУБД).

**Подзапросы** - запросы, вложенные в другой запрос.

**Типы подзапросов:**

1. **Скалярные подзапросы**: возвращают одно значение.
2. **Многозначные подзапросы**: возвращают список значений (используются с IN, ANY, ALL).
3. **Коррелированные подзапросы**: зависят от внешнего запроса.

## 12. Группирование результатов запроса

**Группирование результатов запроса** используется для объединения строк с одинаковыми значениями в указанных столбцах и применения агрегатных функций к группе.

Для фильтрации после группировки используется `HAVING`. Аналог `WHERE`, но применяется к агрегатам.

## 13. Использование предложения UNION

**Предложение `UNION`** в SQL используется для объединения результатов двух или более `SELECT`-запросов в один набор данных.

**Особенности:**

1. `UNION` исключает дубликаты строк по умолчанию.
2. Количество столбцов и их типы должны совпадать в объединяемых запросах.
3. Для включения дубликатов строк используется `UNION ALL`.

## 14. Соединения, теоретико-множественные и специальные операции над отношениями на примерах оператора SELECT

1. **Соединения:**
    - `INNER JOIN`: возвращает строки, у которых есть совпадения в обеих таблицах.
    - `LEFT JOIN`: возвращает все строки из левой таблицы и совпадающие строки из правой.
    - `RIGHT JOIN`: возвращает все строки из правой таблицы и совпадающие строки из левой.
    - `FULL OUTER JOIN`: возвращает все строки из обеих таблиц (если поддерживается СУБД).
2. **Теоретико-множественные операции:**
    - `UNION`: возрвращает результат двух запросов без дублирования строк. Можно добавить `ALL` для включения дубликатов.
    - `INTERSECT`: возвращает строки, общие для двух запросов.
    - `EXCEPT`: возвращает строки, которые есть в 1-м запросе, но отсутствуют во 2-м.
3. **Специальные операции:**
    - `CROSS JOIN`: возвращает декартово произведение 2-х таблиц.
    - `SELF JOIN`: таблица соединяется сама с собой.
    - `EXISTS`: возвращает `TRUE`, если подзапрос возвращает строки.
    - **Деление**: находит строки, которые связаны со всеми значениями из другой таблицы.

## 15. Представления

**Views (Представления)** - виртуальные таблицы, создаваемые на основе запроса. Они не хранят данные, а отображают результаты выполнения SQL-запроса.

**Создание представления:**

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

**Преимущества:**

1. Упрощает сложные запросы.
2. Один раз созданное представление может использоваться в разных запросах.
3. Обеспечивает стабильность приложения при изменении структуры БД.

**Ограничения:**

1. Нельзя использовать представления для вставки, обновления или удаления данных, если запрос сложный.
2. Производительность зависит от исходного запроса.

## 16. Хранимые процедуры

**Хранимые процедуры** - это сохранённые на стороне сервера наборы SQL-команд, которые можно многократно вызывать для выполнения сложных операций.

**Пример создания процедуры:**

```sql
CREATE PROCEDURE procedure_name (param1 datatype, param2 datatype)
BEGIN
    -- code here
END;
```

**Пример вызова процедуры:**

```sql
CALL procedure_name(param1, param2);
```

**Преимущества:**

1. **Повторное использование:** Снижение дублирования кода.
2. **Скорость:** Процедуры выполняются на сервере, уменьшая сетевые задержки.
3. **Безопасность:** Упрощённое управление доступом через права на вызов процедур.
4. **Инкапсуляция логики:** Бизнес-логика скрыта от пользователей.

**Ограничения:**

1. Отладка хранимых процедур может быть сложной.
2. Выполнение зависит от СУБД, так как синтаксис может отличаться.

## 17. Триггеры

**Триггеры** - это специальные процедуры в БД, которые выполняются автоматически при определённых событиях (вставка, обновление, удаление).

**Пример создания триггера:**

```sql
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON table_name
FOR EACH ROW
BEGIN
    -- code here
END;
```

**Способы применения:**

1. **Логирование изменений.**
2. **Автозаполнение поля.**
3. **Проверка данных.**

**Недостатки:**

1. **Сложность отладки и тестирования.**
2. **Производительность может снижаться при большом количестве операций.**
3. **Могут вызывать рекурсию, если не прописаны изменения.**

## 18. Методы совместного доступа к базам данных. Терминология, типы параллелизма

**Совместный доступ к БД** обеспечивает одновременную безопасную работу нескольких пользователей.

**Терминология:**

1. **Транзакция** - последовательность операций, выполняемых, как единое целое.
2. **Изоляция** - степень защиты транзакций друг от друга.
3. **Concurrency** - одновременное выполнение транзакций.
4. **Locking** - механизм предотвращения одновременного изменения данных.
5. **Deadlock** - ситуация, когда транзакции ожидают выполнения друг друга, что блокирует выполнение.

**Методы совместного доступа к БД:**

1. **Многопользовательский доступ к данным** : подразумевает одновременное выполнение двух и более запросов к одним и тем же объектам данных (таблицам, блокам и т.п.).
2. **Системы распределенной обработки данных**: параллельный доступ нескольких пользователей к одной БД,  расположенной на одной машине, соответствует режиму распределенного доступа к централизованной БД.
3. **Системы распределенных баз данных**: параллельный доступ нескольких пользователей к БД, распределенной по нескольким компьютерам, расположенным в сети, соответствует режиму с параллельного доступа к распределенной БД.

**Типы параллелизма:**

1. **Параллелизм на уровне запроса:** несколько запросов выполняются одновременно.
2. **Параллелизм на уровне транзакций:** одновременное выполнение нескольких транзакций.
3. **Параллелелизм на уровне операций:** Разбиение сложных операций на подоперации, выполняемые параллельно.

## 19. Транзакции и блокировки. Свойства, способы завершения транзакций

**Транзакция** - это последовательность операций с БД, которая выполняется, как единое целое.

**Блокировка** - это механизм синхронизации, предотвращающий одновременное изменение или чтение данных.

**Свойства транзакций:**

1. **Atomicity:** все операции транзакций выполняются, как единое целое или не выполняются вовсе.
2. **Consistency:** после выполнения транзакции данные остаются в согласованном состоянии.
3. **Isolation**: результаты транзакции недоступны другим транзакциям до её завершения.
4. **Durability:** данные, зафиксированные транзакцией, сохраняются даже в случае сбоя системы.

**Блокировки:**

1. **Shared Lock**: позволяет другим транзакциям читать, но запрещает изменение.
2. **Exclusive Lock:** запрещает другим транзакциям читать или изменять данные.

**Способы завершения транзакций:**

1. `COMMIT`: фиксирует изменения.
2. `ROLLBACK`: откатывает изменения.

## 20. Параллельное выполнение транзакций

**Параллельное выполнение транзакций** - это процесс одновременного выполнения нескольких транзакций в БД.

**Проблемы параллельности:**

1. **Dirty Read:** транзакция читает данные, которые изменены, но не зафиксированы другой транзакцией.
2. **Non-Repeatable Read:** транзакция читает данные, которые были изменены другой транзакцией.
3. **Phantom Read:** транзакция видит новые строки, добавленные другой транзакцие при повторном запросе.

**Методы обеспечения параллельности:**

1. **Механизмы блокировок:**
    - **Shared Lock** - позволяет читать, но не изменять данные.
    - **Exclusive Lock** - предотвращает доступ других транзакций к данным.
2. **Управление версионированием:** каждая транзакция видит свою версию данных, а не текущие изменения.
3. **Таймштампы:** временные метки для определения порядка транзакций.
4. **Оптимистический контроль:** Конфликты проверяются при фиксации транзакции, без блокировок.

## 21. Методы сериализации транзакций

**Сериализация транзакций** - это обеспечение выполнения транзакций в таком порядке, который эквивалентен их последовательному выполнению.

**Основные методы сериализации:**

1. **Управление блокировками:** используются для синхронизации транзакций.
2. **Timestamp-Based протоколы:** каждой транзакции присваивается уникальный timestamp для определения её порядка.
3. **Оптимистические протоколы:** предпологается, что конфликты редки, и транзакции выполняются без блокировок.
4. **Версионирование данных:** каждая транзакция работает со своей версией данных.

## 22. Проблема тупиковых ситуаций и её решение

**Deadlock** - это состояние при котором две или более транзакций блокируют друг друга, ожидая освобождения ресурсов, занятых другой транзакцией.

**Возможные решения тупиков:**

1. СУБД автоматически проверяет блокировки и выявляет тупиковые транзакции, при обнаружении тупика одна из транзакций ролбэчится.
2. Использование timestamp'ов для определения приоритета транзакций.

## 23. Уровни изолированности пользователей

**Isolation Levels** определяют степень защиты данных от влияния других параллельных транзакций.

**Уровни изоляции:**

1. **Read Uncommitted:** транзакция может читать данные, изменённые, но не зафиксированные другой транзакцией. Минимальный уровень защиты, подходит для анализа данных, где точность не критична.
2. **Read Committed:** транзакция читает только зафиксированные данные. Часто используется в системах, где требуется баланс между производительностью и целостностью.
3. **Repeatable Read:** транзакция гарантирует, что данные, которые она читает не изменятся другой транзакцией. Сценарии, где важна неизменность прочитанных данных, например, расчёт балансов.
4. **Serializable:** полная изоляция транзакций. Каждая транзакция выполняется как будто последовательно. Требуется в системах с высокой критичностью данных, но снижает производительность.

## 25. Распределенные методы обработки данных. Достоинства и недостатки реляционных СУБД. Постреляционные СУБД

**Достоинства:**

1. Простота представления и формирования БД.
2. Универсальность и удобство обработки данных  с помощью SQL.

**Недостатки:**

1. Сложность моделирования предметной области.
2. Ограниченность в структурах представления данных.
3. Недостаточность возможностей по работе со сложными данными.
4. Отсутствие специальных механизмов навигации.

**Особенности постреляционных СУБД:**

1. Отменено требование атомарности атрибутов.
2. Используют трёхмерные структуры.
3. Возмоеости по описанию сложных объектов реального мира.
4. В качестве языка запросов используется расширенный SQL, позволяющий извлекать сложные объекты из одной таблицы без операций соединения.

## 26.Распределенные базы данных (РБД). Задачи. Проблемы

**Задачи:**

1. Решить проблему масштабирования.
2. Предоставить возможность для работы с БД посредством интернет-сервисов.
3. Построить в облаке проект реляционной БД со всеми преимуществами облачных технологий.

**Проблемы:**

1. **Проблема оптимизации:** в РБД нельзя применит обычные правила оптимизации инструкций SQL - программа оптимизации должна знать параметры сети и, в частности её быстродействие.
2. **Проблема совместимости данных:** В различных вычислительных системах разные типы данных. Данные одного типа в разных форматах.
3. **Оборудование от разных поставщиков:** различные СУБД -> различные диалекты SQL.

## 27. NoSQL. Особенности NoSQL: нереляционный, свободная схема, простой API, распределенный.

**NoSQL** значит Not only SQL. Может быть применён для расширения возможности БД, где SQL недостаточно гибок, и сохранён там, где SQL справляется со своими задачами. в NoSQL мы жертвуем согласованностью данных ради доступности и масштабируемости.

**Свободная схема** в  NoSQL означает, что база данных не требует заранее определённой структуры данных, как это принято в традиционных реляционных базах данных (SQL).

**Простой API** в NoSQL - это способ взаимодействия с базой данных, который делает работу разработчика проще, снижая сложность и предоставляя инструменты для быстрого и интуитивного доступа к данным. REST API - лишь один из популярных примеров этого подхода.

**Распределенный:**

- Несколько NoSQL БД могут быть выполнены распределённым способом.
- Возможности автоматического масштабирования и переключения при сбое.
- Часто жертвуют концепцией ACID ради масштабируемости и пропускной способности.
- В большинстве случаев отсутствует синхронная репликация между распределенными узлами.
- Архитектура не определена - это обеспечивает меньшую координацию и более высокое распределение.