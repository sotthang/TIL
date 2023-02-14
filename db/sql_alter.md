# SQL ALTER

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

## Table Field 추가

```sql
ALTER TABLE mysql_test_a ADD note TEXT;
```

|Field|Type|Null|Key|Default|Extra|
|-|-|-|-|-|-|
|id|int|NO|PRI||auto_increament|
|title|varchar(30)|NO||||
|price|int|NO||||
|amount|int|NO||||
|note|text|YES||||

## Table Field 변경

```sql
ALTER TABLE mysql_test_a MODIFY note VARCHAR(100);
```

|Field|Type|Null|Key|Default|Extra|
|-|-|-|-|-|-|
|id|int|NO|PRI||auto_increament|
|title|varchar(30)|NO||||
|price|int|NO||||
|amount|int|NO||||
|note|varchar(100)|YES||||

## Table Field 명 변경

```sql
ALTER TABLE mysql_test_a CHANGE COLUMN note refer VARCHAR(100);
```

|Field|Type|Null|Key|Default|Extra|
|-|-|-|-|-|-|
|id|int|NO|PRI||auto_increament|
|title|varchar(30)|NO||||
|price|int|NO||||
|amount|int|NO||||
|refer|varchar(100)|YES||||

## Table Field 삭제

```sql
ALTER TABLE mysql_test_a DROP COLUMN refer;
```

|Field|Type|Null|Key|Default|Extra|
|-|-|-|-|-|-|
|id|int|NO|PRI||auto_increament|
|title|varchar(30)|NO||||
|price|int|NO||||
|amount|int|NO||||
