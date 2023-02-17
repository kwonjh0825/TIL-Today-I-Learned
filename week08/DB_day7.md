> 오늘 내용은 실습 문제 풀이 중 혼자 찾아본 함수들을 정리한 것

# IFNULL

- `IFNULL(COLUMN, DEFAULT)` 와 같은 형식
- 해당 column의 값이 NULL이면 DEFAULT 값을 출력하고, 그렇지 않다면 해당 column의 값을 출력
- CASE문을 활용하여 비슷하게 구현 가능
    
    ```sql
    CASE
    	WHEN COLUMN IS NULL THEN DEFAULT
    	ELSE COLUMN
    END 
    ```
    

# 소수점 처리 관련 함수

- ROUND
  - `ROUND(value, [i])` 와 같은 형식
  - i가 양수라면 value에 대하여 소수점 아래 i+1 번째 자리에서 반올림, i가 없다면 소수점 첫 번째 자리에서 반올림
    - ex) `ROUND(23000.1234, 1)`: 소수점 아래 2번째 자리에서 반올림한 23000.1 을 반환
  - i가 음수라면 value에 대하여 -i 번째 자리에서 반올림
    - ex) `ROUND(21231, -1)`: 첫 번째 자리에서 반올림한 21230을 반환
- TRUNCATE
  - `TRUNCATE(value, i)`와 같은 형식
  - i가 양수라면 value에 대하여 소수점 아래 i+1번째 자리까지 버림
      - ex) `TRUNCATE(3414.43215, 1)`: 소수점 아래 두 번째 자리까지 버린 3414.4 반환
  - i가 음수라면 value에 대하여 -i 번째 자리까지 버림
    - ex) `TRUNCATE(23115, -2)`: 두 번째 자리까지 버린 23100 반환

# 문자열 나누기 / 자르기

- LEFT
  - `LEFT(string, i)`와 같은 형식
  - string 의 왼쪽부터 i개의 문자 반환
    - ex) `LEFT('A123452345', 2)`: 왼쪽에서 2개인 A1 반환
- SUBSTRING
  - `SUBSTRING(string, i, j)`와 같은 형식
  - string 의 i번째 문자부터 j 길이만큼 잘라냄
    - ex) `SUBSTRING('abcdefgh', 1, 3)`: 1번째 문자부터 길이가 3만큼 잘라낸 abc 반환
- RIGHT
  - `RIGHT(string, i)` 와 같은 형식
  - string 의 오른쪽 i개 문자 반환
    - ex) `RIGHT('abcdefg', 3)`: 오른쪽에서 3개인 efg 반환