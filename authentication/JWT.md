## JWT란

- 인증에 필요한 정보들을 암호화 시킨 JSON 토큰
- JWT 기반 인증은 JWT Access Token을 HTTP 헤더에 실어 서버가 클라이언트를 식별하는 방식
- JWT는 JSON 데이터를 Base64 URL-safe Encode를 통해 인코딩하여 직렬화 한 것이며 토큰 내부에는 위변조 방지를 위해 개인 키를 통한 전자서명도 들어 있음
- JWT는 인증(위조 방지)가 목적

### JWT의 구조

- `.`을 구분자로 나누어지는 세 가지 문자열의 조합
- `Header.Payload.Signature` 의 세 가지로 구성되어 있다.

### Header

- JWT에서 사용할 타입과 해시 알고리즘의 종류가 담겨 있음

### Payload

- 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨 있음
- 토큰에서 사용할 정보 조각인 claim(key-value 형식으로 이루어진 한 쌍의 정보)이 담겨 있음
- 정해진 데이터 타입은 없지만, 대표적으로 Registered claims, Public claims, Priavte claims로 나뉨
- Registered claims
    - 미리 정의된 클레임
    - 구조
        - iss: 이슈 발행자
        - exp: 만료 시간
        - sub: 제목
        - iat: 이슈 발행 시간
        - jti: JWT ID
- Public claims
    - 사용자가 정의할 수 있는 클레임 공개용 정보 전달을 위해 사용
- Private claims
    - 해당하는 당사자들 간에 정보를 공유하기 위해 만들어진 사용자 지정 클레임.
    - 외부에 공개되어도 상관없지만 해당 유저를 특정할 수 있는 정보를 담음

### Signature

- Header, Payload를 Base64 URL-safe Encode 한 이후 Header에 명시된 해시 함수를 적용하고,
개인 키로 서명한 전자서명이 담겨 있음
- 헤더에서 정의한 알고리즘 방식을 활용
- (header + payload)와 서버가 갖고 있는 유일한 key 값을 합친 것을 헤더에서 정의한 알고리즘으로 암호화
- header, payload는 단순히 인코딩된 값이기 때문에 제3자가 복호화, 조작할 수 있지만, signature는 서버 측에서 관리하는 비밀 키가 유출되지 않는 한 복호화될 수 없음
- 토큰의 위변조 여부를 확인하는 데 사용

### JWT 인증 과정

1. 사용자가 서버에 로그인 인증을 요청
2. 서버에서 요청을 받으면 header, payload, signature 를 정의
3. header, payload, signature를 각각 Base64로 한 번 더 암호화하여 JWT를 생성하고 이를 쿠키에 담아 클라이언트로 전송
4. 클라이언트는 서버로부터 받은 JWT를 로컬에 저장(쿠키 또는 다른 저장소), API를 서버에 요청 시 Authorization header에 Access Token을 담아 전송
5. 서버가 요청을 받을 시 header에 담긴 JWT가 서버에서 발행한 토큰인지 일치 여부 확인, 일치한다면 payload에 들어있는 유저 정보를 클라이언트에 응답
6. Access Token의 시간이 만료되면 클라이어트는 Refresh Token을 이용해 서버로부터 새로운 Access Token을 발급받음

### 토큰 인증이 신뢰성을 갖는 이유

- 클라이언트로부터 받은 JWT header, payload 를 서버의 key값을 이용해 signature를 다시 만들고 비교
- 대조 결과를 통해 유저 정보가 조작되었는지 알 수 있음

### JWT 장점

- 데이터 위변조를 막을 수 있음
- 인증 정보에 대한 별도의 저장소가 필요없음
- 토큰에 대한 기본 정보와 전달할 정보 및 토큰이 검증되었음을 증명하는 서명 등 필요한 모든 정보를 자체적으로 지니고 있음
- 서버가 stateless가 되어 서버 확장성이 우수해질 수 있음
- 토큰 기반으로 다른 로그인 시스템에 접근 및 권한 공유 가능
- OAuth의 경우, 소셜 계정을 통해 다른 웹서비스에서도 로그인 가능
- 모바일 어플래케이션 환경에서도 잘 동작

### JWT 단점

- 토큰 자체에 정보를 담고 있어 양날의 검이 될 수 있음
- 토큰의 payload에 3종류의 claim을 저장, 정보가 많아질수록 토큰의 길이가 늘어나 네트워크에 부하
- payload는 암호화된 것이 아니라 Base64로 인코딩된 것이기 때문에 payload가 탈취당하면 디코딩 후 데이터를 볼 수 있음. payload에 중요 데이터를 넣지 말아야 함
- stateless 한 특성이 있기 때문에 토큰은 클라이언트 측에 관리 및 저장. 토큰을 탈취당하면 대처하기 어려움

### Access Token, Refresh Token

- 토큰 탈취의 위험성 떄문에 그대로 사용하지 않고 이중으로 나누어 인증하는 방식 채택
- Access Token
    - 클라이언트가 가지고 있는 실제 유저의 정보가 담긴 토큰
    - 클라이언트에서 요청이 오면 서버에서 해당 토큰에 있는 정보를 활용하여 사용자 정보에 맞게 응답 진행
- Refresh Token
    - 짧은 수명을 가지는 Access Token에게 새로운 Access Token을 발급해주기 위해 사용되는 토큰
    - 보통 DB에 유저 정보와 같이 기록