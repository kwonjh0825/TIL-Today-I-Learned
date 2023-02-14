# 테이블 생성

- `CREATE TABLE` 를 통해 생성 가능
- 테이블 생성 예시
    
  ```sql
  CREATE TABLE table_name (
  	column_1 data_type, 
  	column_2 data_type, 
  	...,
  	constraints
  )
  ```
    
  - 각 필드에 적용할 데이터 타입 설정
  - 테이블 및 필드에 적용할 제약조건(constraints) 작성
  - 제약조건에는 Primary Key, Foreign Key 등 설정 가능
- 대표적인 MySQL Data Type
  - Numeric(숫자형)
    - `INT`, `FLOAT`, …
  - String(문자형)
    - `VARCHAR`, `TEXT`, …
  - Date and Time(날짜형)
    - `DATE`, `DATETIME`, …
- Constraint(제약조건)
  - 데이터의 무결성(정확성과 일관성 보증)을 지키기 위해 데이터를 입력받을 때 실행하는 검사 규칙
  - 대표적 제약조건
    - `PRIMARY KEY`
    - `NOT NULL`
- `AUTO_INCREMENT` attribute
  - 기본 키 필드에 사용 가능
  - 테이블의 기본 키에 대한 번호를 자동 생성
  - 고유한 숫자를 부여
  - 시작 값은 1이며, 데이터 입력 시 값을 생략하면 자동으로 1씩 증가
  - 이미 사용한 값은 재사용되지 않음
  - 기본적으로 NOT NULL

# 테이블 삭제

- `DROP TABLE`을 통해 삭제 가능
- 테이블 삭제 예시
    
    ```sql
    DROP TABLE table_name;
    ```
    

# 테이블 조작

- `ALTER TABLE`을 통해 테이블 필드 조작(생성, 수정, 삭제)
  - 필드 추가: `ALTER TABLE ADD`
  - 필드 속성 변경: `ALTER TABLE MODIFY`
  - 필드 이름 변경: `ALTER TABLE CHANGE COLUMN`
  - 필드 삭제: `ALTER TABLE DROP COLUMN`
- 필드 추가
    
    ```sql
    ALTER TABLE 
    	table_name
    ADD 
    	new_column_name column_definition;
    ```
    
  - ADD 이후 새 필드 이름과 데이터 타입, 제약조건 작성
- 필드 속성 변경
    
    ```sql
    ALTER TABLE
    	table_name
    MODIFY
    	column_name column_definition;
    ```
    
- 필드 이름 변경
    
    ```sql
    ALTER TABLE
    	table_name
    CHANGE COLUMN
    	old_column_name new_column_name column_definition;
    ```
    
  - 항상 column definition을 추가해 줘야 함
- 필드 삭제
    
    ```sql
    ALTER TABLE
    	table_name
    DROP COLUMN
    	column_name;
    ```
    

# 데이터 조작

- 데이터 삽입
  - `INSERT`를 통해 테이블에 레코드 삽입
    
    ```sql
    INSERT INTO table_name (c1, c2, ...)
    VALUES (v1, v2, ...);
    ```
    
    - `INSERT INTO` 절 다음에 테이블 이름, 괄호 안에 필드 목록 작성
    - `VALUES` 다음 괄호 안에 필드에 삽입할 값 목록 작성
    - `INSERT INTO` 의 필드 목록과 `VALUES` 의 필드 목록의 순서는 같아야함
    - `AUTO_INCREMENT` 속성은 NULL 입력으로 건너뛸 수 있음
    - `CURDATE()`: 현재 날짜 반환, MySQL 내장 함수
- 데이터 수정
  - `UPDATE`를 통해 테이블의 레코드 수정
    
    ```sql
    UPDATE table_name
    SET column_name = expression,
    [WHERE 
    	condition];
    ```
    
    - `SET`뒤에 수정할 필드와 새 값을 지정
    - `WHERE` 절에서 수정할 레코드를 지정할 조건 작성, 조건이 없다면 모든 레코드 수정
    - `REPLACE` 를 통해 문자열 일부를 변경 가능
      
      ```sql
      UPDATE articles
      SET
      	content=REPLACE(content, 'content', 'TEST');
      ```
        
- 데이터 삭제
  - `DELETE`를 통해 테이블의 레코드 삭제
    
    ```sql
    DELETE
    FROM table_name
    [WHERE conditions];
    ```
    
    - `WHERE` 절을 작성하지 않으면 모든 레코드 삭제