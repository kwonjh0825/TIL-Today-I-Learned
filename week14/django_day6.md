## ORM

- Object-Relational-Mapping
- 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간 데이터를 변환하는 프로그래밍 기술

## QuerySet API

- ORM에서 데이터를 검색, 필터링, 정렬 및 그룹화 하는데 사용하는 도구
- API를 사용하여 SQL이 아닌 Python 코드로 데이터 처리
- 구문
    - `'Model class'.'Manager'.'Queryset API'`

### Query

- 데이터베이스에 특정 데이터를 보여 달라는 요청
- 쿼리문 작성 → 원하는 데이터를 얻기 위해 데이터베이스에 요청을 보낼 코드 작성
- 파이썬으로 작성한 코드가 ORM 에 의해 SQL로 변환되어 데이터베이스에 전달되며 데이터베이스의 응답 데이터를 ORM이 QuerySet이라는 자료 형태로 변환하여 우리에게 전달

### QuerySet

- 데이터베이스에게서 전달 받은 객체 목록(데이터 모음)
- 순회 가능한 데이터로써 1개 이상의 데이터를 불러와 사용할 수 있음
- Django ORM을 통해 만들어진 자료형
- 데이터베이스가 단일한 객체를 반환할 때에는 QuerySet이 아닌 Model 의 Instance로 반환

## ORM Create

### Django Shell

- django 환경 안에서 실행되는 python shell
- 입력하는 QuerySet API 구문이 django 프로젝트에 영향을 미침

### 객체 생성

- 첫번째 방법
    
    ```python
    article = Article()
    article.title = 'first'
    article.content = 'django'
    article.save()
    ```
    
- 두번째 방법
    
    ```python
    article = Article(title='second', content='django')
    article.save()
    ```
    
- 세번째 방법
    
    ```python
    article.object.create(title='third', content='django')
    ```
    

## OEM Read

- get
    - 단일 데이터 조회
    - 객체를 찾을 수 없으면 DoesNotExist 예외 발생
    - 둘 이상의 객체를 찾으면 MultipleObjectsReturned 예외 발생
- filter
    - 특정 조건 데이터 조회
- field lookups
    - 특정 레코드에 대한 조건을 설정
    - field(), exclude(), get() 에 대한 키워드 인자로 지정됨
    - contains, startswith 등