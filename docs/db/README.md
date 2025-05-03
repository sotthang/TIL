# DB (DataBase)

## DB 란

데이터의 집합 또는 저장소

## DBMS (DataBase Management System) 란

데이터베이스를 운영, 관리하는 시스템 (오라클, mysql 등)

## RDM & RDBMS (Relational DataBase & Relational DataBase Management System) 란

- RDB : 관계형 데이터의 집합, key 와 value 의 관계를 테이블화 (2차원 형태) 한 것
- RDBMS : 관계형 데이터베이스를 운영, 관리하는 시스템으로 table 이라는 최소 단위로 구성되어 있음
- table : 행 (row, recore, tuple) 과 열 (column, field, attribute) 로 이루어진 데이터 저장 단위
- 행 (row, recore, tuple) : 관계된 데이터의 묶음
- 열 (column, field, attribute) : 유일한 이름을 가지며 필드의 데이터 타입 (정수, 텍스트 등) 지정 가능
- Primary Key : table 에서 행의 식별자로 이용되는 열을 Key 또는 Primary Key (식별이 되어야 하기에 중복이 없는 유일한 값이어야 함)
- Foreign Key : table 의 필드 중 다른 table 의 행을 식별할 수 있는 key

![rdb_table](rdb_table.png)

### table 간의 관계

![rdb_relation](rdb_relation.png)

## 리스트

- [SQL](sql.md)
  - [CREATE](sql_create.md)
  - [DROP](sql_drop.md)
  - [INSERT](sql_insert.md)
  - [SELECT 1](sql_select_1.md)
  - [SELECT 2](sql_select_2.md)
  - [ALTER](sql_alter.md)
  - [UPDATE](sql_update.md)
  - [DELETE](sql_delete.md)
  - [JOIN](sql_join.md)
  - [Subquery](sql_subquery.md)
  - [TRANSACTION](sql_transaction.md)
  - [TRIGGER](sql_trigger.md)
  - [Normalization](sql_normalization.md)
  - [ERD](sql_erd.md)
- [NoSQL](nosql.md)

