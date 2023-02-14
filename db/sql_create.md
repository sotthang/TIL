# SQL CREATE

## Database 생성

```sql
CREATE DATABASE DB_test;
```

## Database 접속

```sql
USE DB_test;
```

## Table 생성

```sql
CREATE TABLE mysql_test_a ( 
id INT(6) NOT NULL AUTO_INCREMENT PRIMARY KEY, 
title VARCHAR(30) NOT NULL, 
price INT(11) NOT NULL,
amount INT(11) NOT NULL,
note TEXT, 
created_at DATE
); 
```

데이터타입
- INT : 숫자형
- VARCHAR(30) : 가변 문자 길이 30
- CHAR(10) : 고정 문자 길이 10
- DATE : 년월일 (YYYY-MM-DD)
- TIME : 시간 (HH:MM:SS)
- DATETIME : 년월일 + 시간 (YYYY-MM-DD HH:MM:SS)
- TIMESTAMP 년월일 + 시간 (YYYYMMDDHHMMSS)

제약조건
- NOT NULL : 데이터가 반드시 존재해야 함
- AUTO_INCREMENT : 1부터 번호 자동 생성 (이미 사용한 값은 재사용 안하며 NOT NULL 조건)
- PRIMARY KEY : 기본키 지정
