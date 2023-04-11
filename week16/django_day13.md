## Many to one relationships

- N:1 or 1:N 관계
- 한 테이블의 0개 이상의 레코드가 다른 테이블의 레코드 한 개와 관련된 관계
- ex) Comment(N) - Article(1) 관계
    - 0개 이상의 댓글은 1개의 게시글에 작성될 수 있다

### ForeignKey(to, on_delete)

- django에서 N:1 관계 설정 모델 필드
- 인스턴스 이름은 참조하는 모델 클래스 이름의 단수형(소문자)로 작성 권장
- to: 참조하는 모델 class 이름
- on_delete
    - 참조하는 model class가 삭제될 때 연결된 하위 객체 동작 결정
    - 외래 키가 참조하는 객체(1)이 사라졌을 때 외래 키를 가진 객체(N)을 어떻게 처리할 지 결정(데이터 무결성)
    - CASCADE: 부모 객체가 삭제되었을 때 이를 참조하는 객체도 삭제

### 역참조

- 나를 참조하는 테이블을 참조 하는 것
- N:1 관계에서는 1이 N을 참조하는 상황
- article.comment_set.all()

### Related manager

- N:1 혹은 M:N 관계에서 역참조 시 사용하는 manager
- N:1 관계에서 생성되는 related manager의 이름은 `참조하는 모델명_set` 과 같은 규칙

### save(commit=False)

- 인스턴스를 create하지만 DB에 저장하지 않고 인스턴스만 반환