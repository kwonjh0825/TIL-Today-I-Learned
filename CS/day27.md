## CORS

- Cross-Origin Resource Sharing
- 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
    - 출처는 protocol, domain, port 로 구성됨
- 악의를 가진 사용자가 소스코드를 보고 CSRF(Cross-Site Request Forgery)나 XSS(Cross-Site Scripting)과 같은 방법을 사용해 정보를 탈취하는 것을 방지하기 위함

### 동작 방식

- 프리플라이트 요청
    - 요청을 예비 요청과 본 요청으로 나눔
    - OPTION 메서드를 통해 다른 도메인의 리소스에 요청이 가능한지 확인 후 가능하다면 실제 요청 전송
- 단순 요청
    - 프리플라이트 요청과 다르게 요청을 보내면서 즉시 Cross Origin인지 확인
    - 아래 조건을 모두 충족해야 함
        - 메서드는 GET, POST, HEAD 중 하나
        - 헤더는 Accept, Accept-Language, Content-Langauge, Content-Type 만 허용
        - Content-Type 헤더는 다음의 값만 허용
            - application/x-www-form-urlencoded
            - multipart/form-data
            - text/plain
- 인증정보 포함 요청
    - 인증 관련 헤더를 포함할 때 사용하는 요청
    - 브라우저가 제공하는 비동기 리소스 요청 API인 XMLHttpRequest 객체나 fetch API는 별도의 옵션 없이 브라우저의 쿠키 정보나 인증과 관련된 헤더를 기본적으로 요청에 담지 않기 때문에 credential 옵션을 변경하지 않고서는 cookie를 주고받을 수 없음
    - 옵션
        - omit: 절대로 cookie를 전송하거나 받지 않음
        - same-origin: 동일 출처라면 user credential(cookie, basic http auth 등)을 전송
        - include: cross-origin 이라고 할지라도 언제나 user credentials 전송