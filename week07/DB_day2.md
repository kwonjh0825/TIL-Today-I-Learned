# SQL

- SQL(Structure Query Language): 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- 관계형 데이터베이스와 소통하는 언어
- SQL Syntax
  - SQL 키워드는 대소문자를 구분하지 않음(명시적 구분을 위해 대문자 권장)
  - SQL statements 끝에는 세미콜론이 필요

# SQL statements

- SQL statements 유형
  - DDL(Data Definition Language)
    - 데이터 정의
    - 데이터의 기본 구조 및 형식 변경
    - `CREATE`, `DROP`, `ALTER`
  - DQL: 데이터 검색
    - 데이터 검색
    - `SELECT`
  - DML: 데이터 조작
    - 데이터 조작(추가, 수정, 삭제)
    - `INSERT`, `UPDATE`, `DELETE`
  - DCL: 데이터 제어
    - 데이터 및 작업에 대한 사용자 권한 제어
    - `COMMIT`, `ROLLBACK`, `GRANT`, `REVOKE`

# 용어 정리

- Query
  - 질의, 질문
  - 데이터베이스로부터 정보를 요청하는 것
  - 일반적으로 SQL로 작성하는 코드를 쿼리문(SQL문)이라고 함
- SQL 표준
  - SQL은 ANSI(미국 국립표준협회)와 ISO(국제 표준화기구)에 의해 표준이 채택됨
  - 널리 사용되는 모든 RDBMS에서 SQL 표준 지원
  - RDBMS별로 독자적 기능에 따라 표준을 벗어나는 문법이 존재

# Querying data

- SELECT
  - 테이블에서 데이터를 조회
  - Syntax
    - `SELECT select_list FROM table_name;`
    - `SELECT` 키워드 다음 데이터를 선택하려는 필드를 하나 이상 지정(전부 조회 시 *)
    - `FROM` 키워드 다음 데이터를 선택하려는 테이블의 이름 지정
  - 실행 순서: FROM → SELECT → ORDER BY

# Sorting data

- ORDER BY
  - 조회 결과의 레코드 정렬
  - `FROM` 절 뒤에 위치
  - 하나 이상의 컬럼을 기준으로 결과를 오름차순, 내림차순으로 정렬 가능
  - ASC: 오름차순(기본)
  - DESC: 내림차순
