# SQL INSERT

```sql
CREATE TABLE mysql_test_a ( 
id INT(6) NOT NULL AUTO_INCREMENT PRIMARY KEY, 
title VARCHAR(30) NOT NULL, 
price INT(11) NOT NULL,
amount INT(11) NOT NULL,
date_at DATE
);
```

## Table Data 추가

```sql
INSERT INTO mysql_test_a (id, title, price, amount, date_at) VALUES ('1', 'short_pants', '30000', '5', '2020-02-02');
INSERT INTO mysql_test_a (id, title, price, amount) VALUES ('2', 'blue_jeans', '50000', '20');
INSERT INTO mysql_test_a (id, title, price, amount) VALUES ('3', 'skirt', '60000', '10'), ('4', 'short_t_shirt', '15000', '10');
```

|id|title|price|amount|date_at|
|---|----|-----|------|-------|
|1|short_pants|30000|5|2020-02-02|
|2|blue_jeans|50000|20||
|3|skirt|60000|10||
|4|short_t_shirt|15000|10||

```sql
INSERT INTO mysql_test_a (title, price, amount, date_at) VALUES ('blue_jeans', '34000', '13', CURDATE());
-- CURDATE() : 오늘 날짜 반환 함수
```

|id|title|price|amount|date_at|
|---|----|-----|------|-------|
|1|short_pants|30000|5|2020-02-02|
|2|blue_jeans|50000|20||
|3|skirt|60000|10||
|4|short_t_shirt|15000|10||
|5|blue_jeans|34000|13|2023-02-14|
