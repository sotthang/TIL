# SQL SELECT

## DB

```sql
SELECT * FROM mysql_test_a;
```

|id|firstname|lastname|lastloginData|
|--|---------|--------|-------------|
|1|John|Doe|2020-01-01|
|2|King|Jean|2020-01-11|
|3|Young|Jeff|2020-01-21|
|4|King|Julie|2020-04-22|
|5|Young|Julie|2020-04-23|
|6|Young|Mary|2021-03-15|
|7|Holz|Mihael|2021-03-15|
|8|Brown|Julie|2021-11-03|
|9|Brown|Ann|2021-12-25|
|10|Brown|William|2022-04-15|

## Table Data 중복 제거

```sql
SELECT DISTINCT firstname FROM mysql_test_a;
```

|firstname|
|-|
|John|
|King|
|Young|
|Holz|
|Brown|

## Table 특정 조건 검색

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a WHERE firstname = 'Young';
```

|firstname|lastname|lastloginData|
|-|-|-|
|Young|Jeff|2020-01-21|
|Young|Julie|2020-04-23|
|Young|Mary|2021-03-15|

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a WHERE firstname != 'Young';
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|John|Doe|2020-01-01|
|King|Jean|2020-01-11|
|Holz|Mihael|2021-03-15|
|Brown|Ann|2021-12-25|
|Brown|William|2022-04-15|

```sql
SELECT id, firstname, lastname FROM mysql_test_a WHERE id < 4;
```

|id|firstname|lastname|
|--|---------|--------|
|1|John|Doe|
|2|King|Jean|
|3|Young|Jeff|

```sql
SELECT id, firstname, lastname FROM mysql_test_a WHERE id BETWEEN 5 AND 8;
```

|id|firstname|lastname|
|--|---------|--------|
|5|Young|Julie|
|6|Young|Mary|
|7|Holz|Mihael|
|8|Brown|Julie|

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a WHERE lastloginDate LIKE '2020%';
-- lastloginDate 에서 2020으로 시작하는 값 검색
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|John|Doe|2020-01-01|
|King|Jean|2020-01-11|
|Young|Jeff|2020-01-21|
|King|Julie|2020-04-22|
|Young|Julie|2020-04-23|

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a WHERE lastloginDate LIKE '%15';
-- lastloginDate 에서 15 로 끝나는 값 검색
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|Young|Mary|2021-03-15|
|Holz|Mihael|2021-03-15|
|Brown|William|2022-04-15|

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a WHERE firstname LIKE '___g';
-- firstname 값이 4자리이면서 g 로 끝나는 값 검색
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|King|Jean|2020-01-11|
|King|Julie|2020-04-22|

## Table 조회 갯수 제한

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a LIMIT 3;
-- 조회 결과 중 상위 3개 검색
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|John|Doe|2020-01-01|
|King|Jean|2020-01-11|
|Young|Jeff|2020-01-21|

```sql
SELECT firstname, lastname, lastloginDate FROM mysql_test_a LIMIT 2, 5;
-- 조회 결과 중 상위 2개는 출력하지 않고 그 다음 5개 검색
```

|firstname|lastname|lastloginData|
|---------|--------|-------------|
|Young|Jeff|2020-01-21|
|King|Julie|2020-04-22|
|Young|Julie|2020-04-23|
|Young|Mary|2021-03-15|
|Holz|Mihael|2021-03-15|

## Table 그룹화

```sql
SELECT firstname FROM mysql_test_a GROUP BY firstname;
```

|firstname|
|-|
|John|
|King|
|Young|
|Holz|
|Brown|

```sql
SELECT firstname, COUNT(*) FROM mysql_test_a GROUP BY firstname;
firstname 에서 각 데이터들의 갯수 검색
```

|firstname|COUNT(*)|
|-|-|
|John|1|
|King|2|
|Young|3|
|Holz|1|
|Brown|3|


## Table 그룹화 후 특정 Data 확인

```sql
SELECT * FROM mysql_test_a;
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|
|5|blue_jeans|45000|3|
|6|blue_jeans|99000|1|
|7|blue_jeans|76000|12|
|8|short_t_shirt|35000|6|

```sql
SELECT title, AVG(amount) FROM mysql_test_a GROUP BY title HAVING AVG(amount) > 5;
-- 그룹화 시 WHERE 대신 HAVING 사용
```

|title|AVG(amount)|
|-|-|
|blue_jeans|9.0000|
|skirt|10.0000|
|short_t_shirt|8.0000|
