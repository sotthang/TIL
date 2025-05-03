# SQL TRANSACTION

명령어를 한번에 실행시킬 때 사용하며 단 하나의 명령어라도 에러가 생기면 반영되지 않음

## TRANSACTION 특징

- 원자성 (Atomicity) : 트랜잭션의 결과는 DB에 반영이 되거나 반영이 안되거나 이 두 가지 결과만 존재
- 일관성 (Consistency) : 트랜잭션이 진행되는 동안 DB가 변경되더라도 이전에 사용한 DB를 참조 (즉, 트랜잭션은 시작부터 종료 시까지 같은 형태의 DB를 참조)
- 독립성 (Isolation) : 트랜잭션이 두 개 이상 실행될 때 트랜잭션끼리 영향을 주지 못함 (즉, 하나의 트랜잭션이 또 다른 트랜잭션의 결과를 참조할 수 없음)
- 영구성 (Durability) : 트랜잭션이 성공적으로 완료(Commit) 되었을 때 결과를 영구적으로 DB에 반영

## commit

|id|name|
|-|-|
|1|John|
|2|David|

```sql
START TRANSACTION;
INSERT INTO `mysql_test_a` (`name`) VALUES ('Mary');
COMMIT;
SELECT * FROM mysql_test_a;
```

|id|name|
|-|-|
|1|John|
|2|David|
|3|Mary|

## rollback

|id|name|
|-|-|
|1|John|
|2|David|

```sql
START TRANSACTION;
INSERT INTO `mysql_test_a` (`name`) VALUES ('Mary');
ROLLBACK;
SELECT * FROM mysql_test_a;
```

|id|name|
|-|-|
|1|John|
|2|David|
