## 제3 정규화

- 다음 규칙을 만족해야 함
    1. 2 정규형을 만족해야 함
    2. 기본키를 제외한 속성들 간 이행 종속성이 없어야 함
- 이행 종속성: A→B, B→C일 때 A→C 가 성립

## BCNF

- Boyce-Codd Normal Form
- 제 3정규화를 조금 더 강화한 버전
- 다음 규칙을 만족해야 함
    1. 3 정규형을 만족해야 함
    2. 모든 결정자가 후보 키 집합에 속해야 함