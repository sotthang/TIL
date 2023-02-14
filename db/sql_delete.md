# SQL DELETE

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
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
