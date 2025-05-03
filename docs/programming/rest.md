# REST (Representational State Transfer)

## REST 란

네트워크 상에서 Client 와 Server 사이의 통신 방식 중 하나로 자원을 이름(표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것

- 자원 : 소프트웨어가 관리하는 모든 것 (문서, 그림, 데이터, 해당 소프트웨어 자체 등)
- 표현 : 자원을 표현하기 위한 이름 (자원-DB의 학생 정보, 표현-students)
- 상태 : 데이터가 요청되는 시점에 자원의 상태를 전달

웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일

## 구성 요소

- 자원(Resource): URI
  - 모든 자원에 고유한 ID 가 존재하고, 이 자원은 Server 에 존재
  - 자원을 구별하는 ID 는 /groups/:group_id 같은 HTTP URI
  - Client 는 URI 를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server 에 요청
- 행위(Verb): HTTP Method
  - HTTP 프로토콜의 Method를 사용 (GET, POST, PUT, DELETE 등)
- 표현(Representation of Resource)
  - Client 가 자원의 상태에 대한 조작을 요청하면 Server 는 이에 적절한 응답(Representation)을 보냄
  - REST 에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 나타냄
  - JSON 혹은 XML를 통해 데이터를 주고 받는 것이 일반적

## 장단점

장점
- HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구출할 필요가 없음
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용 가능
- REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악 가능
- 서버와 클라이언트의 역할을 명확하게 분리

단점
- 표준이 존재하지 않음
- HTTP Method 형태가 제한적

## REST API

REST 기반으로 서비스 API를 구현한 것
- REST 기반으로 시스템을 분산해 확장성과 재사용성을 높여 유지보수 및 운용 편리
- HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현 가능
- REST API 를 제작하면 자바, C#, 웹 등을 이용해 클라이언트를 제작 가능

### REST API 설계

- 슬래시(/)는 계층 관계를 나타내는데 사용
  - ex) http://restapi.example.com/houses/apartments
- URI 마지막 문자로 슬래시(/)를 포함하지 않음
  - URI 에 포함되는 모든 글자는 리소스의 유일한 식별자로 사용되어야 하며 URI가 다르다는 것은 리소스가 다르다는 것이고, 역으로 리소스가 다르면 URI도 달라져야 함
- 하이픈(-)은 URI 가독성을 높이는데 사용
  - 불가피하게 긴 URI 경로를 사용하게 된다면 하이픈을 사용해 가독성을 높임
- 밑줄(_)은 URI 에 사용하지 않음
- URI 경로에는 소문자를 사용
  - RFC 3986(URI 문법 형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정하기 때문
- 파일확장자는 URI 에 포함하지 않음
  - Accept header를 사용한다.
    - ex) http://restapi.example.com/members/soccer/345/photo.jpg (X)
    - ex) GET / members/soccer/345/photo HTTP/1.1 Host: restapi.example.com Accept: image/jpg (O)
- 리소스 간에는 연관 관계가 있는 경우
  - /리소스명/리소스 ID/관계가 있는 다른 리소스명
    - ex) GET : /users/{userid}/devices

## RESTful

REST 아키텍처를 구현하는 웹 서비스를 RESTful 웹 서비스라고 함 (즉, REST 원리를 따르는 시스템을 RESTful이란 용어로 지칭)

RESTful 하지 못한 경우

- CRUD 기능을 모두 POST 로만 처리하는 API
- route 에 resource, id 외의 정보가 들어가는 경우(/students/updateName)
