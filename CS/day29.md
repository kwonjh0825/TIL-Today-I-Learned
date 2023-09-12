# 

## NoSQL

- 비관계형 데이터베이스를 지칭
- 관계형 데이터베이스 지양, 대량 분산된 데이터를 저장 / 조회에 특화되었으며, 스키마 없이 사용 가능하거나 느슨한 스키마를 제공하는 저장소
- 관계형 데이터베이스의 한계를 극복하기 위한 데이터 저장소의 새로운 형태

### 특징

- RDBMS와 달리 데이터 간 관계를 정의하지 않음(JOIN 연산이 불가능)
- RDBMS에 비해 대용량의 데이터 저장 가능(PB 급)
- 여러 곳의 서버에 데이터를 분산 저장하는 분산형 구조로 특정 서버에 장애가 발생했을 때도 데이터 유실 혹은 서비스 중지가 발생하지 않음
- 고정되지 않은 테이블 스키마를 가짐

### 장점

- RDBMS에 비해 저렴한 비용으로 분산처리와 병렬 처리 가능
- 비정형 데이터 구조 설계로 설게 비용 감소
- 빅데이터 처리에 효과적
- 가변적 데이터 구조로 데이터 저장 가능
- 데이터 모델의 유연한 변화 가능

### 단점

- 데이터 업데이트 중 장애가 발생하면 데이터 손실 발생 가능
- 많은 인덱스를 사용하려면 충분한 메모리 필요. 인덱스 구조가 메모리에 저장
- 데이터 일관성이 항상 보장되지 않음

### 종류

- Key-Value DB
    - 기본적 패턴으로 Key-Value의 묶음으로 저장되는 구조
    - 단순한 구조라 속도가 빠르며 분산저장 시 용이
    - Key 안에 (Column, Value) 형태로 된 여러 개의 필드(Column Families)를 가짐
    - 주로 server config, session clustering 등에 사용
    - 엑세스 속도는 빠르지만 scan에는 용이하지 않음
    - ex) Redis, Oracle NoSQL Database, VoldeMorte
- Wide-Column Database
    - 키와 해당 값을 저장할 때마다 각각의 행에 다른 값, 다른 수의 스키마를 가질 수 있음
    - 대량의 데이터 압축, 분산처리, 집계 쿼리 및 쿼리 동작 속도, 확장성이 뛰어난 장점
    - ex) Hbase, GoogleBigTable, Vertica
- Document Database
    - 테이블의 스키마 유동적. 레코드마다 다른 스키마를 가질 수 있음
    - XML, JSON과 같은 Document를 이용해 레코드 저장
    - 트리형 구조로 레코드 저장, 검색에 효과적
    - ex) MongoDB, CouchDB, Azure Cosmos DB
- Graph Database
    - 데이터를 노드로 표현, 노드 사이의 관계를 엣지로 표현
    - 일반적으로 RDBMS보다 성능이 좋고 유연, 유지보수에 용이
    - Social networks, Network diagrams 등에 사용 가능
    - ex) Neo4j, BlazeGraph, OrientDB