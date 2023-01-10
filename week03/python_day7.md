# 사용자 정의 함수

- 함수의 기본 구조
  - 선언과 호출
  - 입력
  - 범위
  - 결과값
- 함수의 선언과 호출
  - 선언은 `def` 키워드 활용
  - 들여쓰기를 통해 Function Body(실행 될 코드블럭) 생성
  - Docstring은 body 앞에 선택적으로 작성
  - 함수는 parameter를 넘겨줄 수 있음
  - 함수는 동작 후 return 을 통해 결과값을 전달
  - 함수는 `함수명()` 을 통해 호출
- parameter : 함수를 실행할 때 함수 내부에서 사용되는 식별자
- argument : 함수를 호출할 때 넣어주는 값

# 함수의 입력(input)

- 기본적으로 함수 호출 시 argument는 위치에 따라 함수 내에 전달됨
- keyword argument
  - 직접 변수의 이름으로 특정 argument를 전달할 수 있음
- Default Arguments value
  - 기본값을 지정하여, 함수 호출 시 argument 값을 설정하지 않도록 함
  - 정의된 것보다 더 적은 개수의 argument들로 호출될 수 있음
- 정해지지 않은 개수의 keyword argument
  - 함수가 임의의 개수의 argument를 keyword argument로 호출될 수 있도록 지정
  - argument들은 딕셔너리로 묶여 처리됨
  - parameter에 `**` 를 붙여 표현

# 함수의 결과값(output)

- 함수는 반드시 값을 하나만 return(명시적 return 이 없는 경우에도 None 반환)
- 함수는 return 과 동시에 실행이 종료됨

# 함수의 범위(scope)

- 함수는 코드 내부에 local scope 생성, 그 외 공간인 global scope로 구분
- Scope
  - global scope : 코드 어디에서든 참조할 수 있는 공간
  - local scope : 함수가 만든 scope, 함수 내부에서만 참조 가능
- variable
  - global variable : global scope에 정의된 변수
  - local variable : local scope 에 정의된 변수
- 객체 생명 주기
  - 객채는 각자의 수명 주기가 존재
  - built-in scope → 파이썬이 실행된 이후부터 영원히 유지
  - global scope →  모듈이 호출된 시점 이후 혹은 인트프리터가 끝날 때까지 유지
  - local scope → 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지
