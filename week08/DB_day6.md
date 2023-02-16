# Subquery

- A query inside query
- 단일 쿼리문에 여러 테이블의 데이터를 결합하는 방식
- 특징
  - 조건에 따라 하나 이상의 테이블에서 데이터를 검색하는 데 사용
  - SELECT, FROM, WHERE, HAVING 등 다양한 맥락에서 사용

# EXISTS

- 쿼리 문에서 반환된 레코드의 존재 여부를 확인

```sql
SELECT
	select_list
FROM 
	table
WHERE
	[NOT] EXISTS (subquery);
```

- subquery 가 하나 이상의 행을 반환하면 EXISTS 연산자가 true를 반환하고, 그렇지 않다면 false 반환
- 주로 WHERE 절에서 subquery 의 반환 값 존재 여부를 확인하는 데 사용

# CASE

- SQL 문에서 조건문을 구성

```sql
CASE case_value
	WHEN when_value1 THEN statements
	WHEN when_value2 THEN statements
...
	[ELSE else_statements]
END CASE;
```

- case_value가 when_value와 같은 것을 찾을 때까지 순차적으로 비교
- when_value가 동일한 case_value를 찾으면 해당 THEN 절의 코드 실행
- 동일한 값을 찾지 못하면 ELSE 절 코드 실행, ELSE 절이 없을 때 동일한 값을 찾지 못하면 에러 발생