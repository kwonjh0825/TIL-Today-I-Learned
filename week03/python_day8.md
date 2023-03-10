# 객체 지향 프로그래밍

- 객체
  - 객체는 특정 타입의 인스턴스
- 객체의 특징
  - type : 어떤 연산자(operator)와 조작(method)이 가능한가?
  - attribute : 어떤 상태(데이터)를 가지는가?
  - method :  어떤 행위(함수)를 할 수 있는가?
- 객체 지향 프로그래밍
  - 프로그램을 여러 개의 독립된 객체들과 그 객체들 간 상호작용으로 파악하는 프로그래밍 방법
  - 데이터와 메소드 분리
  - 추상화된 구조
  - 장점
    - 프로그램을 유연하고 변경이 용이하게 만듬 → 대규모 소프트웨어 개발에 많이 사용됨.
    - 소프트웨어 개발, 보수를 간편하게 만듬
    - 보다 직관적인 코드 분석 가능

# 객체의 요소

- 클래스 : 객체들의 분류
- 인스턴스 : 하나하나의 실체
- 속성 : 특정 데이터 타입 또는 클래스의 객체들이 가지게 될 상태 또는 데이터를 의미
- 메서드 : 특정 타입 혹은 클래스의 객체에 공통적으로 적용 가능한 행위(함수)
- 객체 비교
  - `==`
    - 동등(equal)한지 여부
    - 변수가 참조하는 객체가 내용이 같은 경우 True
  - `is`
    - 동일한지(identical) 여부
    - 두 변수가 동일한 객체를 가리키는 경우 True

# 인스턴스

- 인스턴스 변수
  - 인스턴스가 개인적으로 가지고 있는 속성
  - 각 인스턴스의 고유한 변수
  - 생성자 메서드에서 `self.<name>` 으로 정의
    - 생성된 이후 `<instance>.<name>` 으로 접근 및 할당
- 인스턴스 메서드
  - 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메서드
  - 클래스 내부에 정의되는 메서드의 기본
  - 호출 시 첫 번째 인자로 `self` 가 전달됨
  - `self`
    - 인스턴스 자기 자신을 의미함
      - 파이썬에서 인스턴스 메서드는 첫 번재 인자로 인스턴스 자신이 전달됨
      - 매개변수 이름으로 `self` 를 첫 번째 인자로 정의(암묵적 규칙)
  - 생성자 메서드
    - 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
    - 인스턴스 변수들의 초기값 설정
    - `__init__`
  - 소멸자 메서드
    - 인스턴스 객체가 소멸되기 직전에 호출되는 메서드
    - `__del__`
  - 매직 메서드
    - `__` 로 감싸진 메서드는 특수한 동작을 위해 만들어진 메서드
    - 특정 상황에 자동으로 불리는 메서드
