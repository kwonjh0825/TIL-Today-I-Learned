## 일급 함수

- 함수 자체를 인자로써 다른 함수에 전달하거나 다른 함수의 결과 값으로 리턴할 수 있고, 함수를 변수에 할당하거나 데이터 구조 안에 저장할 수 있는 함수를 뜻함
- 다음의 조건을 만족하는 경우
    - 함수가 object 유형의 인스턴스 인 경우
    - 함수를 변수에 저장할 수 있는 경우
    - 함수를 다른 함수에 매개변수로 전달할 수 있는 경우
    - 함수에서 다른 함수를 반환할 수 있는 경우
    - list, dict 등과 같은 데이터 구조에 저장할 수 있는 경우
- 함수형 프로그래밍에 속하는 방법
    - 함수형 프로그래밍을 사용하면 코드를 간결하게 작성할 수 있어 개발시간을 단축할 수 있음
    - 부작용을 허용하지 않는 순수 함수를 지향
    - 동시에 여러 스레드에서 문제 없이 동작하는 프로그램을 쉽게 작성할 수 있음

### Python 함수 특징

- 실행 시점에 런타임 초기화
- 함수를 변수에 할당 가능
- 함수를 다른 함수의 인자로 전달 가능
    - 익명함수 lambda를 쓸 때에는 가급적 주석 다는 것 권장
- 함수 결과 반환(return) 가능

## 클로저(Closure)

- 자신을 둘러싼 스코프(네임스페이스)의 상태값을 기억하는 함수
- 다음의 조건을 만족하는 경우
    - 해당 함수는 어떤 함수 내의 중첩된 함수여야 함
    - 해당 함수는 자신을 둘러싼 함수 내의 상태값을 반드시 참조해야 함
    - 해당 함수를 둘러썬 함수는 이 함수를 반환해야 함
- 특징
    - 자신을 둘러싼 함수 스코프의 상태값을 참조하는데, 이 값은 함수가 메모리에서 사라져도 유지됨
    - 클로저에서 자신 안에 정의된 내부 변수가 아닌 둘러싸고 있는 변수에 접근 지원
- 장점
    - 관리, 책임을 명확히 할 수 있음
    - 각 변수가 섞여 불필요한 충돌 방지 가능
    - 사용 환경에 맞게 임의대로 내부구조 조정 가능
