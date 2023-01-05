# Dictionary

- 키-값(key-value) 쌍으로 이뤄진 모음(collection)
- key : 불변 자료형만 가능(리스트, 딕셔너리 등은 불가능)
- value : 어떠한 형태든 관계 없음
- 키와 값은 ‘:’ 로 구분됨. 개별 요소는 ‘,’ 로 구분
- 변경 가능(mutable), 반복 가능(iterable)
- 키를 삭제할 때는 .pop()을 활용하여 삭제하고자 하는 키를 전달
- keys() → key로 구성된 결과
- values() → value로 구성된 결과
- items() → (key, value) 의 튜플로 구성된 결과

# 모듈

- 모듈 : 다양한 기능을 하나의 파일로 만든 것
- 패키지 : 다양한 파일을 하나의 폴더로 만든 것
- 라이브러리 : 다양한 패키지를 하나의 묶음으로 만든 것

# 파이썬 표준 라이브러리

- 파이썬에 기본적으로 설치된 모듈과 내장 함수
- random
    - 의사 난수 생성
    - `random.randint(a, b)` → a이상 b이하의 임의의 정수 반환
    - `random.choice(seq)` → 비어 있지 않은 시퀀스에서 임의의 요소를 반환
    - `random.shuffle(seq)` → 시퀀스를 제자리에서 섞음
    - `random.sample(population, k)` → 무작이 비복원 추출 결과인 k 길이의 리스트 반환
- datetime
    - 날짜와 시간을 조작하는 객체를 제공
    - 사용 가능 데이터 타입
        - `datetime.date`
        - `datetime.time`
        - `datetime.datetime`
        - `datetime.timedelta`
    - `datetime.date(y, m, d)` → 모든 인자가 필수, 날짜 반환
    - `datatime.date.today()` → 현재 지역 날짜를 반환
    - `datetime.datetime.today()` → 현재 지역 datetime 반환
- os
    - 운영체제 조작 위한 인터페이스
    - `os.listdir(path='.')` : path 디렉터리에 있는 항목들의 이름을 담고 있는 리스트 반환
    - `os.mkdir(path)` : path 디렉터리 생성
    - `os.chdir(path)` : path 변경

# 디버깅

- 에러
    - 에러 메시지가 발생하는 경우
    - 로직 에러가 발생하는 경우 : 명시적 에러 메시지 없이 예상과 다른 결과가 나온 경우
- branches → 모든 조건이 원하는대로 동작하는지
- for loops → 반복문에 진입하는지, 원하는 횟수만큼 실행되는지
- while loops → for loops와 동일, 종료 조건이 제대로 동작하는지
- function → 함수 호출 시, 함수 파라미터, 함수 결과

# 에러와 예외

- 문법 에러(Syntax error)
    - SyntaxError가 발생하면 프로그램은 실행되지 않음
    - 파일 이름, 줄 번호, `^` 를 통해 문제가 발생한 위치를 표현
- 예외(Exception)
    - 실행 도중 예상치 못한 상황을 맞이하면 프로그램 실행을 멈춤, 문장이나 표현식이 문법적으로 올바르더라도 발생하는 에러
    - 실행 중 감지되는 에러를 예외(Exception)이라 부름
    - 여러 가지 타입으로 나타나고 타입이 메시지의 일부로 출력됨
    - 모든 내장 예외는 Exception Class를 상속받아 이뤄짐
    - 사용자 정의 예외를 만들어 관리할 수 있음
- 예외처리
    - try 문 / except 절을 이용하여 예외 처리 가능
    - try 문
        - 오류가 발생할 가능성이 있는 코드 실행
        - 예외가 발생하지 않으면 except 없이 실행 종료
    - except 문
        - 예외가 발생하면 except 절이 실행
        - 예외 상황을 처리하는 코드를 받아 적절한 조치를 취함
    - 예외 발생 시키기
        - `raise <표현식> (메시지)`
        - `assert <표현식>, <메시지>` : 일반적으로 디버깅 용도로 사용.
        - raise vs assert
            - raise : 실제 프로덕션 코드에서 활용
            - assert : 특정 조건이 거짓이면 발생. 디버깅 및 테스트에서 활용