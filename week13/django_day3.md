## Django Template System

- 데이터 표현을 제어하면서 표현과 관련된 로직을 담당

## Django Template Language

- Template에서 조건, 반복, 변수, 필터 등의 프로그래밍적 기능을 제공하는 시스템

### Syntax

- Variable
    - view 함수에서 render 함수의 세 번째 인자로 dictionary 타입으로 넘겨받을 수 있음
    - dictionary key 에 해당하는 무자열이 template에서 사용 가능한 변수명이 됨
    - . 을 사용하여 변수 속성에 접근할 수 있음
    - `{{ variable }}` 와 같이 사용
- Filters
    - 표시할 변수를 수정할 때 사용
    - chained 가 가능하며 일부 필터는 인자를 받기도 함
    - 약 60개의 built-in template filters 를 제공
    - `{{ variable | filter }}` 와 같이 사용
- Tags
    - 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
    - 일부 태그는 시작과 종료 태그 필요
    - 약 24개의 built-in template tags를 제공
    - 출력되지 않음
    - `{% tag %}` 와 같이 사용

## 템플릿 상속

- 페이지의 공통 요소를 포함하고 하위 템플릿이 재정의 할수 있는 공간을 정의하는 기본 skeleton 템플릿을 작성하여 상속 구조를 구축

### extends

- 자식(하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
- 반드시 템플릿 최상단에 작성되어야 함
- 2개 이상 사용 불가
- `{% extends 'path' %}` 와 같이 사용

### block

- 하위 템플릿에서 재정의(overridden) 할 수 있는 블록 정의
- 하위 템플릿이 작성할 수 있는 공간 지정
- `{% block name %} {% endblock name %}` 와 같이 사용

## 요청과 응답

### form

- 사용자로부터 할당된 데이터를 서버로 전송
- 웹에서 사용자 정보를 입력하는 여러 방식을 제공

### action, method

- form 의 핵심 속성 2가지
- 데이터를 어디(action)로 어떤 방식(method)로 보낼 지 결정
- action
    - 입력 데이터가 전송될 URL(목적지) 지정
    - 지정하지 않으면 데이터는 현재 form 이 있는 페이지의 URL 로 보내짐
- method
    - 어떤 방식으로 보낼 것인지 정의
    - HTTP request method 지정(GET, POST)

### input

- 사용자의 입력을 받을 수 있는 요소
- type 속성값에 따라 다양한 유형의 입력 데이터를 받음

### name

- input 의 핵심 요소
- 데이터를 제출했을 때 서버는 name 속성에 설정된 값을 통해 사용자가 입력한 데이터에 접근할 수 있음

### Query String Parameters

- 사용자의 입력 데이터를 URL 주소에 파라미터를 통해 넘기는 방법
- 문자열은 `&` 로 연결된 `key=value` 쌍으로 구성되며 기본 URL과 `?` 로 구분됨

### request 객체

- form을 통해 제출된 데이터는 HTTP request 객체에 들어 있음
- `request.GET` 을 통해 dictionary 형식을 받을 수 있음