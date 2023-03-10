# SQL Normalization

## 정규화 란

RDB 설계 단계에서 중복을 최소화하여 데이터를 구조화하는 과정

### 제 1 정규형 (First Normal Form, 1NF)

필드에는 하나의 값만 저장하며 유사한 정보를 저장하는 두 개의 필드가 있으면 분할하여 기본키가 되는 필드를 작성

|주문번호|날짜|이름|연락처|주문상품|
|-|-|-|-|-|
|1|1/5|옥순|010-1111-1111|0001 책상 1개, 0002 시계 10개|
|2|2/1|순자|010-2222-2222|0001 책상 2개, 0002 시계 3개|
|3|2/5|옥순|010-1111-1111|0001 책상 3개, 0003 의자 1개|

주문상품에 여러 개의 값이 존재하므로 제 1 정규형을 만족하지 못함

이를 해결하기 위해 주문상품을 3개의 필드로 분할

|주문번호|날짜|이름|연락처|상품코드|상품명|갯수|
|-|-|-|-|-|-|-|
|1|1/5|옥순|010-1111-1111|0001|책상|1|
|1|1/5|옥순|010-1111-1111|0002|시계|10|
|2|2/1|순자|010-2222-2222|0001|책상|2|
|2|2/1|순자|010-2222-2222|0002|시계|3|
|3|2/5|옥순|010-1111-1111|0001|책상|3|
|3|2/5|옥순|010-1111-1111|0003|의자|1|

유사한 정보가 들어있는 필드들이 있으므로 테이블을 분할

|주문번호|날짜|이름|연락처|
|-|-|-|-|
|1|1/5|옥순|010-1111-1111|
|2|2/1|순자|010-2222-2222|
|3|2/5|옥순|010-1111-1111|

|주문번호|상품코드|상품명|갯수|
|-|-|-|-|
|1|0001|책상|1|
|1|0002|시계|10|
|2|0001|책상|2|
|2|0002|시계|3|
|3|0001|책상|3|
|3|0003|의자|1|

### 제 2 정규형 (Second Normal Form, 2NF)

키를 이용해 데이터를 특정 지을 수 있는 것 (함수 종속성) 을 찾아 테이블 분할

상품명은 상품코드에 종속될 수 있으므로 테이블을 분할

|주문번호|상품코드|상품명|갯수|
|-|-|-|-|
|1|0001|책상|1|
|1|0002|시계|10|
|2|0001|책상|2|
|2|0002|시계|3|
|3|0001|책상|3|
|3|0003|의자|1|

|주문번호|상품코드|갯수|
|-|-|-|
|1|0001|1|
|1|0002|10|
|2|0001|2|
|2|0002|3|
|3|0001|3|
|3|0003|1|

|상품코드|상품명|
|-|-|
|0001|책상|
|0002|시계|
|0003|의자|

### 제 3 정규형 (Third Normal Form, 3NF)

PK 외에 중복이 있으면 테이블 분할

동일한 사람이 여러 번 주문했으므로 테이블을 분할

|주문번호|날짜|이름|연락처|
|-|-|-|-|
|1|1/5|옥순|010-1111-1111|
|2|2/1|순자|010-2222-2222|
|3|2/5|옥순|010-1111-1111|

|주문번호|날짜|고객번호|
|-|-|-|
|1|1/5|1|
|2|2/1|2|
|3|2/5|1|

|고객번호|이름|연락처|
|-|-|-|
|1|옥순|010-1111-1111|
|2|순자|010-2222-2222|

### 정규화 전 후

정규화 전 테이블

|주문번호|날짜|이름|연락처|주문상품|
|-|-|-|-|-|
|1|1/5|옥순|010-1111-1111|0001 책상 1개, 0002 시계 10개|
|2|2/1|순자|010-2222-2222|0001 책상 2개, 0002 시계 3개|
|3|2/5|옥순|010-1111-1111|0001 책상 3개, 0003 의자 1개|

정규화 후 테이블

|주문번호|상품코드|갯수|
|-|-|-|
|1|0001|1|
|1|0002|10|
|2|0001|2|
|2|0002|3|
|3|0001|3|
|3|0003|1|

|상품코드|상품명|
|-|-|
|0001|책상|
|0002|시계|
|0003|의자|

|주문번호|날짜|고객번호|
|-|-|-|
|1|1/5|1|
|2|2/1|2|
|3|2/5|1|

|고객번호|이름|연락처|
|-|-|-|
|1|옥순|010-1111-1111|
|2|순자|010-2222-2222|
