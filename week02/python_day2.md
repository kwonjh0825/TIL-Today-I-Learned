# 형 변환

- 암시적 형 변환
    - 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 반환하는 경우
    - ex) True + 3
- 명시적 형 변환
    - 사용자가 함수를 통해 자료형을 직접 변환하는 경우

# String Formatting

- %-formatting
    - ex) `print('hello, %s' % name)`
- f-string
    - ex) `print(f'hello, {name}')`
- format 함수 활용
    - ex) `print(’hello, {}’.format(name))`

# Range

- 숫자의 시퀀스(범위)를 나타내기 위해 사용
- 기본형 : `range(n)` : 0 부터  n-1 까지
- 범위 지정 : `range(n, m)` : n 부터 m-1 까지
- 범위 및 스텝 지정 : `range(n, m, s)` : n 부터 m-1 까지 s 만큼 증가하며
- 변경 불가능(immutable), 반복 가능(iterable)

# 제어문

- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건) 하거나 계속하여 실행(반복)하는 제어가 필요
- 순서도(Flow chart) 로 표현 가능
- 조건문
    - 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용
    - 조건이 참인 경우 이후 들여쓰기 된 코드 블럭 실행
    - 조건이 거짓이면 else 이후 들여쓰기 된 코드 블럭 실행(else 는 선택적으로 사용 가능)
    - ex) `if <expression>:`
    - 복수 조건문 : elif 를 통해 여러 조건에 따른 코드 작성 가능
    - 중첩 조건문
        - 조건문 내에 조건문이 중첩되어 사용되는 경우

# 반복문

  - 특정 조건을 도달할 때까지 계삭 반복되는 일련의 문장
  - for문
    - 반복 가능한 객체를 모두 순회하면 종료
    - 별도의 종료조건이 필요 없다
    - 순회 가능한 객체 : string, tuple, list, range, set, dictionary, …

  - 반복문 제어

    - break
      - 반복문 종료
    - continue
      - continue 이후 코드 블록은 수행하지 않고 다음 반복을 수행
    - for-else
      - 끝까지 반복문 실행 후 else 문 실행
      - break를 통해 중간에 종료되면 else 문은 실행되지 않음