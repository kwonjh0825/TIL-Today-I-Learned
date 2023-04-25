## 읽기 전용 필드 설정

- read_only_fields 를 사용해 외래 키 필드를 읽기 전용 필드로 설정
- 읽기 전용 필드는 데이터를 전송하는 시점에 해당 필드를 유효성 검사에서 제외시키고 데이터 조회 시에는 출력하도록 함

## 역참조 데이터 조회

- PrimaryKeyRelatedField()
    - serializer는 기존 필드를 override 하거나 추가적인 필드를 구성할 수 있음
- Nested relationships
    - 모델 관계 상으로 참조 된 대상은 참조하는 대상의 표현에 포함되거나 중첩될 수 있음
    - 이러한 중첩 관계는 serializers 필드를 사용하여 표현 가능

## API 문서화

- Swagger
    - REST 웹 서비스를 설계, 빌드, 문서화 등을 도와주는 오픈 소스 소프트웨어 프레임워크