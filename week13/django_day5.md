# Django Model

- DB의 테이블을 정의하고 데이터를 조작할 수 있는 기능들을 제공
- 테이블 구조를 설계하는 청사진(설계 도면)
- django.db.models 모듈의 Model이라는 부모 클래스를 상속 받아 작성
- model 기능에 관련된 모든 설정이 담긴 클래스
- 개발자는 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위함
- 클래스 변수 명
    - 테이블의 각 필드 이름
- model Field 메서드
    - 테이블 필드의 데이터 타입
    - 키워드 인자: 제약 조건 관련 설정

## Migration

- model 클래스의 변경사항(필드 생성, 추가 수정 등)을 DB에 최종 반영하는 방법
- `makemigrations`: model class를 기반으로 설계도(migration) 작성
- `migrate`: 만들어진 설계도를 DB에 전달하여 반영
- 추가 필드 작성
    - 기존 테이블이 존재하기 때문에 필드를 추가할 때 필드의 기본 값 설정이 필요
        - 1번은 직접 기본 값을 입력
        - 2번은 현재 대화에서 나간 후 models.py 에 기본 값 관련 설정을 하는 방법
    - 추가하는 필드의 기본 값 입력
        - 아무것도 입력하지 않고 enter를 누르면 django가 제안하는 기본 값으로 설정됨
- model class에 변경사항이 생겼다면 반드시 새로운 설계도를 생성하고 이를 DB에 반영

### 필드

- `CharField()`
    - 길이의 제한이 있는 문자열을 넣을 때 사용
    - 필드의 최대 길이를 결정하는 `max_length`는 필수 인자
- `TextField()`
    - 글자의 수가 많을때 사용
- `DatetimeField()`
    - 날짜와 시간을 넣을 때 사용
    - 선택 인자
        - `auto_now`: 데이터가 저장될 때마다 자동으로 현재 날짜시간 저장, update에 적합
        - `auto_now_add`: 데이터가 처음 생성될 때만 자동으로 현재 날짜시간을 저장, craete에 적합

# Admin site

## Automatic admin interface

- django는 추가 설치 및 설정 없이 자동으로 관리자 인터페이스 제공

## admin 계정 생성

- `python manage.py createsuperuser`
- 유저 이름, 비밀번호, 이메일 지정 가능