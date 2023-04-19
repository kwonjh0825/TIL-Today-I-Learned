## M:N 관계

- M:N 관계로 맺어진 두 테이블에는 변화 없음
- ManyToManyField는 중계 테이블을 자동 생성
- ManyToManyField는 M:N 관계를 맺는 두 모델 어디에 위치해도 상관 없음, 참조 / 역참조 방향 주의

## ManyToManyField

- many-to-many 관계 설정 시 사용하는 모델 필드
- 모델필드의 RelatedManager를 사용하여 관련 객체 추가, 제거, 생성

### 옵션

- related_name
    - 역참조시 사용하는 manager name 변경
- through
    - 중개 테이블을 직접 작성하는 경우 through 옵션 사용하여 중개 테이블을 나타내는 Django 모델 지정
    - 일반적으로 중개 테이블에 추가 데이터를 사용하는 다대다 관계와 연결하려는 경우 사용됨
- symmetrical
    - ManyToManyField가 동일한 모델을 가리키는 정의에서만 사용
    - 기본값: True

### M:N에서의 methods

- add()
    - 지정된 객체를 관련 객체 집합에 추가
    - 이미 존재하는 관계에 사용하면 관계가 복제되지 않음
- remove()
    - 관련 객체 집합에서 지정된 모델 개체를 제거