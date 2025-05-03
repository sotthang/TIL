# SQL TRIGGER

특정 조건 발생 시 자동으로 코드를 실행할 수 있게 해주는 명령어

```sql
-- 현재 트리거 목록
SHOW TRIGGERS; 

-- 트리거 삭제
DROP TRIGGER 트리거이름;
```

## 테이블 수정 시 특정 컬럼을 자동적으로 현재 시각을 변경해주는 Trigger

|id|name|createdAt|updatedAt|
|-|-|-|-|
|1|dog|2023-02-20 19:45:00|2023-02-20 19:45:00|
|2|cat|2023-02-20 19:45:00|2023-02-20 19:45:00|
|3|cow|2023-02-20 19:45:00|2023-02-20 19:45:00|

```sql
DELIMITER //
CREATE TRIGGER test
BEFORE UPDATE ON articles FOR EACH ROW
BEGIN
SET NEW.updatedAt = CURRENT_TIME();
END//
DELIMITER ;

UPDATE articles SET title = 'cute cat' WHERE id = 2;

SELECT * FROM articles;
```

|id|name|createdAt|updatedAt|
|-|-|-|-|
|1|dog|2023-02-20 19:45:00|2023-02-20 19:45:00|
|2|cute cat|2023-02-20 19:45:00|2023-02-20 19:46:02|
|3|cow|2023-02-20 19:45:00|2023-02-20 19:45:00|
