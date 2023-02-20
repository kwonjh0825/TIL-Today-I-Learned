# Transaction

- 여러 쿼리문을 묶어서 하나의 작업처럼 처리하는 방법
- 쪼개질 수 없는 업무처리의 단위
- 한 쿼리문이 실패하면 전체 transaction이 실패, 전체가 수행되거나 전혀 수행되지 않아야 함
- ex) 계좌이체(인출&입금)
  - 송금 중에 알수 없는 문제로 인해 인출에는 성공했는데 입금에 실패하면 안됨
  - 인출과 입금이 모두 성공하던지 실패해야 함
- Syntax
    
    ```sql
    START TRANSACTION;
    state_ments;
    
    [ROLLBACK|COMMIT];
    ```
    
  - `START TRANSACTION` : 트랜잭션 구문의 시작 알림
  - `COMMIT` : 모든 작업이 정상적으로 완료되면 한꺼번에 DB에 알림
  - `ROLLBACK` : 부분적으로 작업에 실패하면 트랜잭션에서 진행한 모든 연산을 취소하고 트랜잭션 실행 전으로 되돌림

# Trigger

- 특정 이벤트(INSERT, UPDATE, DELETE)에 대한 응답으로 자동으로 실행되는 것
- Syntax
    
    ```sql
    CREATE TRIGGER trigger_name
    {BEFORE | AFTER} {INSERT | UPDATE | DELETE}
    ON table_name FOR EACH ROW
    trigger_body;
    ```
    
  - 트리거가 활성화될 때 실행할 코드를 trigger_body 에 지정
  - 여러 명령문을 실행하려면 `BEGIN` `END` 키워드로 묶어서 사용
    - `DELIMITER`: SQL 구문 문자(;) 변경
    - `DELIMITER //` 를 사용해 문장 종료를 // 로 바꿔 BEGIN - END 사이 다중 구문 수행 가능
  - 특정 시점 전, 후 데이터에 접근할 수 있도록 키워드 제공(OLD, NEW)
