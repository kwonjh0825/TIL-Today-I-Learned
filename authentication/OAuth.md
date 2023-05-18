## OAuth란

- 다양한 플랫폼의 특정 사용자 데이터에 접근하기 위해 제 3자 클라이언트가 사용자의 접근 권한을 위임받을 수 있는 표준 프로토콜

## OAuth 2.0 주체

### Resource Owner

- 리소스 소유자
- 서비스를 이용하면서 타 플랫폼(구글, 페이스북 등)에서 리소스를 소유하고 있는 사용자

### Authorization Server

- Resource Owner를 인증하고, 클라이언트에게 Access token을 발급해주는 서버

### Resource Server

- 구글, 페이스북, 트위터와 같이 리소스를 가지고 있는 서버

### Client

- Resource Server의 자원을 이용하고자 하는 서비스
- 개발자가 개발할 서비스

## 어플리케이션 등록

### Redirect URL 등록

- 승인되지 않은 URL로 redirect될 경우, Authorization Code를 탈취당할 위험이 있기 때문에, OAuth 서비스는 인증이 성공한 사용자를 사전에 등록된 Redirect URL 로만 direct 시킴
- 일부 서비스에서는 여러 Redirect URL 을 등록할 수 있음
- 보안을 위해 기본적으로 https만 허용되지만, loopback(localhost)는 예외적으로 http 허용

### Client ID, Client Secret

- 등록 과정을 마치면 Client ID, Secret 발급
- Access Token을 얻는 데 사용
- Client Secret이 유출되면 심각한 보안 사고로 이어질 수 있음

## OAuth 2.0 동작 매커니즘

### 로그인 요청

- Resource Owner가 ‘구글 로그인’ 등의 버튼을 클릭해 로그인 요청
- Client는 OAuth 프로세스를 시작하기 위해 사용자의 브라우저를 Authorization Server로 전송
- Client는 Authorization Server가 제공하는 Authorization URL에 `response_type`, `client_id`, `redirect_url`, `scope` 등의 매개변수를 쿼리 스트링으로 포함하여 전송
- 매개변수
    - `response_type`: 반드시 `code`로 설정, 인증이 성공한 경우 클라이언트는 Authorization Code를 받을 수 있음
    - `client_id`: 애플리케이션을 생성했을 때 발급받은 Client ID
    - `redirect_url`: 애플리케이션을 생성할 때 등록한 Redirect URL
    - `scope`: 클라이언트가 부여받은 리소스 접근 권한

### 로그인 페이지, ID/PW 제공

- 클라이언트가 빌드한 Authorization URL로 이동된 Resource Owner는 제공된 로그인 페이지에서 ID / PW 등을 입력하여 인증

### Authorization Code 발급, Redirect URL로 이동

- 인증이 성공되었다면, Authorization Server는 제공된 Redirect URL로 사용자를 이동시킴
- Redirect URL에 Authorization Code를 포함하여 사용자를 redirect 시킴
- Authorization Code는 클라이언트가 Access token을 획득하기 위해 사용하는 임시 코드로, 수명이 매우 짧음

### Authorization Code와 Access Token 교환

- Client는 Authorization Server에 Authorization Code를 전달하고 Access Token을 응답받음
- Client는 발급받은 Access Token을 저장하고, Resource Server에서 Resource Owner의 리소스에 접근하기 위해 Access Token을 사용
- Access Token은 유출되면 안 되기 때문에 HTTPS 연결을 통해서만 사용 가능
- Authorization Code와 Access Token 교환은 token 엔드포인트에서 이루어짐
- `application/x-www-form-urlencoded` 형식에 맞춰 전달해야 함
- 필수 매개 변수
    - `grant_type`: 항상 `authorization_code` 로 설정되어야 함
    - `code`: 발급받은 Authorization code
    - `redirect_url`
    - `client_id`
    - `client_secret`: RFC 표준 상 필수는 아니지만 Client Secret이 발급된 경우 포함하여 요청

### 로그인 성공

- Client는 Resource Owner에게 로그인이 성공하였음을 알림

### Access Token으로 리소스 접근

- Resource Owner가 Resource Server의 리소스가 필요한 기능을 Client에 요청
- Client는 위 과정에서 발급받고 저장해 둔 Resource Owner의 Access Token을 사용하여 제한된 리소스에 접근하고 Resource Owner에게 자사 서비스 제공

## OAuth 2.0 scope

- 스코프라는 개념을 통해 유저 리소스에 대한 클라이언트의 접근 범위를 제한
- 스코프는 여러 개가 될 수 있으며, 대소문자를 구분하는 문자열을 공백으로 구분하여 표현

## Authorization Code의 필요성

- Redirect URL을 통해 Authorization Code를 발급하는 과정이 생략되면, Authorization Server가 Access Token을 Client에 전달하기 위해 Redirect URL을 통해야 함
- 이때, Redirect URL을 통해 데이터를 전달할 방법은 URL 자체에 데이터를 실어 전달하는 방법이 유일한데, 브라우저를 통해 데이터가 곧바로 노출됨
- Access Token은 민감한 데이터이기 때문에 쉽게 노출된다면 보안 사고로 이어짐
- 즉 보안 사고 방지 측면에서 Authorization Code 사용