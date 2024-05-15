---
title: "PostgreSQL-Basics"
categories:
    - Others
tags:
    - Database
    - SQL
---

대충 아래 링크 강의에 나오는 것 정도를 정리했다.

https://www.freecodecamp.org/learn/relational-database/learn-relational-databases-by-building-a-mario-database/build-a-mario-database

DB 접속: `psql --username=$USERNAME --dbname=$DBNAME` (bash에서)

## psql 명령어

앞에 `\` 붙어있는 명령어들은 psql에서 사용하는 명령어들이다. 
* DB list 확인: `\l`
* 특정 DB 접속: `\c <DB_NAME>`
* 특정 DB에 접속한 상태에서 table list 확인: `\d`,
* 특정 table의 schema 확인: `\d <TABLE_NAME>`


## SQL 명령어

SQL 쿼리 명령어들 (`CREATE`, `SELECT`, `INSERT`, `UPDATE`, `DELETE` 등)은 뒤에 세미콜론을 붙여야 한다.

### CREATE


* DB 생성:<br>
```sql
CREATE DATABASE <db_name>;
```
* Table 생성:<br>
```sql
CREATE TABLE <table_name> (column1 datatype [constraint], column2 datatype [constraint], ...);
```

### DROP

* Table 삭제:<br>
```sql
DROP TABLE <table_name>;
```
* DB 삭제:<br>
```sql
DROP DATABASE <db_name>;
```

### INSERT

* Tuple 추가:<br>
```sql
INSERT INTO <table_name> (column1, column2, ...) VALUES (value1, value2, ...);
```
한 번에 여러 tuple도 추가할 수 있다.
```sql
INSERT INTO <table_name> (column1, column2, ...)
VALUES
    (value1, value2, ...), 
    (value1, value2, ...),
    ...;
```

### DELETE

* Tuple 삭제:<br>
```sql
DELETE FROM <table_name> WHERE <condition>;
```
    * Equal은 `==`가 아니라 `=`이다.



### ALTER

* Table 이름 변경:<br>
```sql
ALTER TABLE <table_name> RENAME TO <new_table_name>;
```

* DB 이름 변경:<br>
```sql
ALTER DATABASE <db_name> RENAME TO <new_db_name>;
```


* Table scheme 변경:
    * Column 추가:<br>
    ```sql
    ALTER TABLE <table_name> ADD <column_name> <data_type> [<constraint_name>];
    ```
        * 외래 키로 추가
        ```sql
        ALTER TABLE <table_name>
        ADD COLUMN <column_name> <data_type>
        REFERENCES <another_table_name>(<another_column_name>);
        ```
    * Column 삭제:<br>
    ```sql
    ALTER TABLE <table_name> DROP <column_name>;
    ```
    * Column 이름 변경:<br>
    ```sql
    ALTER TABLE <table_name> RENAME COLUMN <column_name> TO <new_column_name>;
    ```
    * Column 타입 변경:<br>
    ```sql
    ALTER TABLE <table_name> ALTER COLUMN <column_name> TYPE <new_data_type>;
    ```


* Column에 constraint 추가:<br>
    * `NOT NULL` constraint 추가:<br>
    ```sql
    ALTER TABLE <table_name> ALTER COLUMN <column_name> SET NOT NULL;
    ```
    * `UNIQUE` constraint 추가:<br>
    ```sql
    ALTER TABLE <table_name> ADD CONSTRAINT <constraint_name> UNIQUE (<column_name>);
    ```
* 특정 Column을 기본 키로 설정:<br>
```sql
ALTER TABLE <table_name> ADD PRIMARY KEY (<column_name>);
```
* 특정 Column을 외래 키로 설정:<br>
```sql
ALTER TABLE <table_name> ADD FOREIGN KEY (<column_name>) REFERENCES <another_table_name>(<another_column_name>);
```

### Update

* Tuple 업데이트:<br>
```sql
UPDATE <table_name> SET column1 = value1, column2 = value2, ... WHERE <condition>;
```

### SELECT

```sql
SELECT column1, column2, ...
    FROM <table_name>
    [WHERE <condition>]
    [ORDER BY column1, column2, ... [ASC|DESC]]
    [LIMIT <number>]
    ;
```
group by, having, join, 집계 함수, 중첩 쿼리 같은 것 까지 여기서 설명하긴 너무 길다. 다른 글에서 다루려면 join에 포스트 하나, 집계 함수에 포스트 하나, 중첩 쿼리에 포스트 하나 정도 될 것 같긴 한데...

### 자료형

* `int`: 다 알고 있을 그거
* `numeric(precision, scale)`: 고정소수점 숫자. precision은 전체 자릿수, scale은 소수점 이하 자릿수
* `serial`: auto-incrementing integer
* `varchar(n)`: 최대 n글자의 가변 길이 문자열
* `text`: 길이 제한 없는 가변 길이 문자열
    * 문자열은 ''로 감싸야 한다. ""는 table, column 이름 같은 데 사용된다.
* `boolean`: `true` 또는 `false`
* `date`: 날짜. `YYYY-MM-DD` 형식 문자열 직접 입력 가능
