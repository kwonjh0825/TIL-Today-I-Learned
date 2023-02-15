# Joining table

- `JOIN`
  - 둘 이상의 테이블에서 데이터를 검색하는 방법
- Join 종류
  - INNER JOIN
  - OUTER JOIN(LEFT, RIGHT)
  - CROSS JOIN
- `INNER JOIN`
  - 두 테이블에서 값이 일치하는 레코드에 대해서만 결과를 반환
    
  ```sql
  SELECT
  	select_list
  FROM
  	table1
  INNER JOIN table2
  	ON table1.fk = table2.pk;
  ```
    
  - FROM 절 이후 메인 테이블 지정
  - INNER JOIN 절 이후 조인할 테이블 지정
  - ON 키워드 이후 조인 조건 작성. 조인 조건은 table1, table2 간의 레코드를 일치시키는 규칙 지정
  - 2중 INNER JOIN 가능
    
    ```sql
    SELECT
        select_list
    FROM
    	table1
    INNER JOIN table2
    	ON table1.fk = table2.pk
    INNER JOIN table3
    	ON table1.fk = table3.pk;
    ```
        
- `OUTER JOIN`
  - `LEFT JOIN`
    - 오른쪽 테이블의 일치하는 레코드와 함께 왼쪽 테이블의 모든 레코드 반환
    - 오른쪽 테이블과 일치하지 않는 컬럼들은 NULL 값들로 채워짐
    - 왼쪽 테이블 한 개의 레코드에 여러 개의 오른쪽 테이블 레코드가 일치할 경우, 해당 왼쪽 레코드를 여러 번 표시
        
    ```sql
    SELECT 
    	select_list
    FROM
    	table1     -- left table
    LEFT [OUTER] JOIN table2     -- right table
    	ON table1.fk = table2.pk;
    ```
        
    - FROM 절 이후 left table 지정
    - LEFT JOIN 절 이후 오른쪽 테이블 지정
    - ON 키워드 이후 조인 조건 작성
  - `RIGHT JOIN`
    - 왼쪽 테이블의 일치하는 레코드와 함께 오른쪽 테이블의 모든 레코드 반환
            
      ```sql
      SELECT 
      	select_list
      FROM
      	table1     -- left table
      RIGHT [OUTER] JOIN table2     -- right table
      	ON table1.fk = table2.pk;
      ```
            
  - `FULL OUTER JOIN`
    - MySQL 에서 해당 문법을 지원하지는 않지만, `UNION` 을 통하여 구현할 수 있음
        
      ```sql
      SELECT
      	select_list
      FROM
      	table1
      LEFT JOIN table2
      	ON table1.fk = table2.pk
      
      UNION
      
      SELECT 
      	select_list
      FROM
      	table1
      RIGHT JOIN tabl2
      	ON table1.fk = table2.pk;
      ```
            
    - `LEFT JOIN` 한 결과와 `RIGHT JOIN` 한 결과를 `UNION`을 통해 합집합 연산을 수행하면 `FULL OUTER JOIN`을 구현할 수 있음