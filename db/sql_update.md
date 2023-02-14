# SQL UPDATE

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|5|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

## Table Data 변경

```sql
UPDATE mysql_test_a SET amount='4' WHERE id='1';
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|4|
|2|blue_jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|

```sql
UPDATE mysql_test_a SET title=REPLACE(title, 'blue_jeans', 'jeans');
-- title column 의 blue_jeans 를 jeans 로 대치
```

|id|title|price|amount|
|---|----|-----|------|
|1|short_pants|30000|4|
|2|jeans|50000|20|
|3|skirt|60000|10|
|4|short_t_shirt|15000|10|




