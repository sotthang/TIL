# SQL SUBQUERY

JOIN 과 비슷하지만 복잡한 쿼리문에는 subquery 사용

성능과 가독성이 좋지 않아 대부분 JOIN 사용

|officecode|country|floor|
|-|-|-|
|100|Korea|3F|
|200|USA|3F|
|300|Spain|12F|
|400|Japan|7F|
|500|Canada|1F|

|id|name|officecode|
|-|-|-|
|1|Minsu|100|
|2|Minji|100|
|3|Mary|200|
|4|David|300|
|5|Yui|400|
|6|Junho|100|
|7|Brad|200|

## Table 2개 Subquery

```sql
SELECT name FROM employees
WHERE officecode = (
SELECT officecode FROM offices WHERE country='Korea'
);
```

|name|
|-|
|Minsu|
|Minji|
|Junho|
