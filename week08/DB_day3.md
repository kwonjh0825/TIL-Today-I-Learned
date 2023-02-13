# Filtering data

- `DISTINCT`
  - `SELECT` 키워드 바로 뒤에 작성
  - 고유한 값 하나씩을 출력(중복 제거)
- `WHERE`
  - 조회 시 특정 검색 조건을 지정
  - `FROM` 절 뒤에 위치
  - 검색 조건은 비교연산자 및 논리연산자를 사용하는 구문이 사용됨
- 비교 연산자
  - `LIKE`
    - 값이 특정 패턴에 일치하는지 확인하는 연산자
    - wildcards와 같이 사용(%, _)
    - Wildcard characters
      - %: 0개 이상의 문자열과 일치하는지 확인
      - _: 단일 문자와 일치하는지 확인
  - `IS`
    - 주로 `IS NULL`과 같이 NULL 값과 비교할 때 사용되는 연산자
- `LIMIT`
  - `LIMIT [offset,] row_count`
  - 하나 또는 두 개의 인자 사용
  - `row_count`는 조회할 최대 레코드 수 지정
- `EXTRACT`
  - 년, 월, 일, 시, 분 등을 추출하는 함수
  - ex) `EXTRACT(YEAR from ex_data) as year`

# Grouping data

- `GROUP BY`
  - 레코드를 그룹화하여 요약본 생성
  - 집계 함수와 같이 사용됨
  - FROM, WHERE 절 뒤에 배치
  - GROUP BY 절 뒤에 그룹화할 필드 목록 작성
  - 집계 함수
    - 값에 대한 계산을 수행하고 단일한 값을 반환
    - `SUM`, `AVG`, `MAX`, `MIN`, `COUNT`
- `HAVING`
  - `GROUP BY`절로 그룹화된 집계 항목에 대하여 세부 조건을 지정할 때 사용