## HTTP Request Methods

- 리소스에 대한 행위를 정의
- HTTP verbs 라고도 함

### 대표 HTTP Request Methods

- GET
    - 서버에 리소스 표현 요청
    - 데이터 조회
- POST
    - 데이터를 지정된 리소스에 제출
    - 서버의 상태 변경
- PUT
    - 요청한 주소의 리소스 수정
- DELETE
    - 지정된 리소스 삭제

### HTTP response status code

- 특정 HTTP 요청이 성공적으로 완료되었는지 여부 나타냄
- 응답은 5개의 그룹으로 나뉨
    - Informational response(100번대)
    - Successful response(200번대)
    - Redirection messages(300번대)
    - Client error response(400번대)
    - Server error response(500번대)

## API

- Application Programming Interface
- 애플리케이션과 프로그래밍으로 소통하는 방법
- API는 복잡한 코드를 추상화하여 대신 사용할 수 있는 몇 가지 더 쉬운 구문 제공

### Web API

- 웹 서버 또는 웹 브라우저를 위한 API
- 현재 웹 개발은 모든 것을 하나부터 열까지 직접 개발하기보다 여러 OpenAPI를 활용하는 추세
- API는 다양한 타입의 데이터 응답

## REST API

- REST라는 API 디자인 아키텍처를 지켜 구현한 API

### REST

- Representational State Transfer
- API server를 개발하릭 위한 일종의 소프트웨어 설계 방법론
- 소프트웨어 아키텍쳐 디자인 제약 모음
- 자원을 정의하고 자원에 대한 주소를 지정하는 전반적인 방법 서술
- REST에서 자원을 정의하고 주소를 지정하는 방법
    - 자원의 식별(URL)
    - 자원의 행위(HTTP Methods)
    - 자원의 표현(궁극적으로 표현되는 결과물, JSON으로 표현된 데이터)

### Django Rest framework

- django에서 Restful API 서버를 쉽게 구축할 수 있도록 도와주는 오픈소스 라이브러리

## Serialization

- 여러 시스템에서 활용하기 위해 데이터 구조나 객체 상태를 나중에 재구성할 수 있는 포맷으로 변환하는 과정
- 어떠한 언어나 환경에서도 나중에 쉽게 사용할 수 있는 포맷으로 변환하는 과정
