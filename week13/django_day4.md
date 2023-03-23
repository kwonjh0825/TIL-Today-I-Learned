# URL dispatcher

- URL 패턴을 정의하고 해당 패턴이 일치하는 요청을 처리할 view 함수를 매핑

## 변수와 URL

### Variable Routing

- URL 일부에 변수를 포함시키는 것
- 변수는 view 함수의 인자로 전달할 수 있음
- `<path_converter:varibale_name>` 와 같이 작성
    - `path_converter`: type(int, str) 지정
    - `str` 생략 가능(명시적으로 작성 권장)

## App과 URL

### APP URL mapping

- 각 앱에 URL 을 정의하는 것
- 프로젝트와 각각의 앱이 URL을 나누어 관리하여 주소 관리를 편하게 하기 위함

### include

- 다른 URL들을 참조할 수 있도록 돕는 함수
- URL의 그 시점까지 일치하는 부분을 잘라내고 남은 문자열 부분을 후속 처리를 위해 include된 URL로 전달

## URL 이름 지정

### Naming URL patterns

- URL에 이름을 지정하는 것
- path 함수의 name 인자를 정의해서 사용

### `url` tag

- 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소 반환
- `{% url 'url-name' arg1 arg2 %}` 와 같이 사용
-