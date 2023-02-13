# SQL SELECT

## Database 생성

```sql
CREATE DATABASE DB_test
```

## Database 접속

```sql
USE DB_test;
```

## Database 삭제

```sql
DROP DATABASE DB_test
```

## Table 생성

```sql
CREATE TABLE mysql_test_a ( 
id INT(6) NOT NULL, 
title VARCHAR(30) NOT NULL, 
price INT(11) NOT NULL,
amount INT(11) NOT NULL
); 
```

## Table Data 추가

```sql
INSERT INTO mysql_test_a (`id`, `title`, `price`, `amount`) VALUES ('1', 'short_pants', '30000', '5');
INSERT INTO mysql_test_a (`id`, `title`, `price`, `amount`) VALUES ('2', 'blue_jeans', '50000', '20'); 
INSERT INTO mysql_test_a (`id`, `title`, `price`, `amount`) VALUES ('3', 'skirt', '60000', '10'); 
INSERT INTO mysql_test_a (`id`, `title`, `price`, `amount`) VALUES ('4', 'short_t_shirt', '15000', '10'); 
```

## Table Data 전체 확인

```sql
SELECT * FROM test
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

## Table Data 특정 column 확인

```sql
SELECT title, price FROM test
```

|title|price|
|----|-----|
|short_pants|30000|
|blue_jeans|50000|
|skirt|60000|
|short_t_shirt|15000|

## Table 특정 Data 확인

```sql
SELECT * FROM mysql_test_a WHERE title='blue_jeans';
```

|title|price|
|----|-----|
|blue_jeans|50000|

## Table Data 정렬

```sql
SELECT * FROM mysql_test_a ORDER BY amount;
-- 오름차순
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|
|2|blue_jeans|50000|20|

```sql
SELECT * FROM mysql_test_a ORDER BY price DESC;
-- 내림차순
```

|id|title|price|amount|
|---|----|-----|------|
|3|skirt|60000|10|
|2|blue_jeans|50000|20|
|1|short_pants|30000|5|
|4|short_t_shirt|15000|10|

### Table column 을 별칭으로 임시변경 후 확인

```sql
SELECT price AS 'money' FROM mysql_test_a;
-- Table 의 column 이름 자체를 변경하는 것이 아닌 결과 출력 할 때만 변경하여 보여줌
```

|money|
|-----|
|30000|
|50000|
|60000|
|15000|

## Table column 간의 사칙연산

```sql
SELECT title, price+amount FROM mysql_test_a;
```

|title|price*amount|
|-----|------------|
|short_pants|30004|
|blue_jeans|50020|
|skirt|60010|
|short_t_shirt|15010|

```sql
SELECT title, price-amount FROM mysql_test_a;
```

|title|price*amount|
|-----|------------|
|short_pants|29996|
|blue_jeans|49980|
|skirt|59990|
|short_t_shirt|14990|

```sql
SELECT title, price*amount FROM mysql_test_a;
```

|title|price*amount|
|-----|------------|
|short_pants|120000|
|blue_jeans|1000000|
|skirt|600000|
|short_t_shirt|150000|

```sql
SELECT title, price/amount FROM mysql_test_a;
```

|title|price*amount|
|-----|------------|
|short_pants|7500.0000|
|blue_jeans|2500.0000|
|skirt|6000.0000|
|short_t_shirt|1500.0000|

## Table Data 변경

```sql
UPDATE mysql_test_a SET amount='4' WHERE id='1';
SELECT * FROM mysql_test_a;
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|4|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

## Table Data 삭제

```sql
DELETE FROM mysql_test_a where id=1;
```

|id|title|price|amount|
|---|----|-----|------|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

## Table Column 확인

```sql
DESC mysql_test_a;
```

|Field|Type|Null|Key|Default|Extra|
|-----|----|----|---|-------|-----|
|id|int|NO|||||
|title|varchar(30)|NO||||
|price|int|NO||||
|amount|int|NO||||

## Table 삭제

```sql
DROP TABLE mysql_test_a;
```
