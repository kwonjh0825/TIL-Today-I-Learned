# HTTP request methods

- 데이터(리소스)에 어떤 요청(행동)을 원하는지를 나타내는 것

## redirect

- `redirect()`
- 인자에 작성된 주소로 다시 요청을 보냄

## HTTP

- 네트워크 상에서 데이터를 주고 받기 위한 약속

## GET method

- 특정 리소스를 조회하는 요청
- GET으로 데이터를 전달하면 Query String 형식으로 보내짐
- 데이터를 가져올 때만 사용해야 함
- 입력 길이에 제한

## POST method

- 특정 리소스에 변경사항을 만드는 요청
- POST로 데이터를 전달하면 HTTP Body에 담겨 보내짐

## CSRF

- Cross-Site-Request-Forgery
- 사이트 간 요청 위조
- 사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여 특정 웹 페이지를 보안에 취약하게 하거나 수정, 삭제 등의 작업을 하게 만드는 공격 방법

## Security Token(CSRF Token)

- 대표적인 CSRF 방어 방법
- 과정
    1. 서버는 사용자 입력 데이터에 임의의 난수 값(token) 부여
    2. 매 요청마다 해당 token 을 포함시켜 전송시키도록 함
    3. 이후 서버에서 요청을 받을 때마다 전달된 token이 유효한지 검증
- `form` tag 아래 `{% csrf_token %}` 를 사용하여 사용자에게 토큰 값 부여
- 요청 시 토큰 값도 함께 서버로 전송될 수 있도록 함
- POST method는 DB에 대한 변경사항을 만드는 요청이기 때문에 토큰을 사용해 최소한의 신원 확인 필요

## Update

- 필요한 view 함수
    - edit: 사용자의 입력을 받는 페이지 렌더링
    - update: 사용자가 입력한 데이터를 받아 DB에 저장