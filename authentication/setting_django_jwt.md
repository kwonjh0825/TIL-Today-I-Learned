## drf-jwt 설치 및 세팅

- django에서 jwt를 구현하는 데 사용되는 라이브러리
- 업데이트가 종료된 drf-jwt 대신 simple-jwt 사용
`pip install djangorestframework-simplejwt`
- settings.py 파일의 INSTALLED_APPS 에 ‘rest_framework_simplejwt’ 추가
- settings.py 파일에 REST_FRAMEWORK 추가
    
    ```python
    REST_FRAMEWORK = {
    	...
    	'DEFAULT_AUTHENTICATION_CLASSES': (
    		...
    		'rest_framework_simplejwt.authentication.JWTAuthentication',
    	)
    	...
    }
    ```
    
- settings.py 파일에 SIMPLE_JWT를 통해 추가적인 JWT_AUTH 설정 가능
    - ACCESS_TOKEN_LIFETIME
        - 엑세스 토큰이 유효한 기간을 지정
        - 현재 UTC 시간에 추가되어 토큰의 기본 ‘exp’ claim 값을 얻음
    - REFRESH_TOKEN_LIFETIME
        - 새로고침 토큰이 유효한 기간을 지정
        - 현재 UTC 시간에 추가되어 토큰의 기본 ‘exp’ claim 값을 얻음
    - ROTATE_REFRESH_TOKENS
        - True로 설정 시, 새로고침 토큰이 TokenRefreshView로 전송될 때 새로운 새로고침 토큰이 새로운 엑세스 토큰과 함께 반환
        - 새로운 새로고침 토큰은 JSON 응답의 refresh 키를 통해 제공됨
    - BLACKLIST_AFTER_ROTATION
        - True로 설정 시, 블랙리스트 앱이 사용 중이고 ROTATE_REFRESH_TOKEN이 True일 경우 새로고침 토큰이 TokenRefreshView에 블랙리스트로 추가됨
        - settings.py 의 INSTALLED_APP에 ‘rest_framework_simplejwt.token_blacklist’ 추가 후 사용 가능
    - UPDATE_LAST_LOGIN
        - True로 설정 시, 로그인 할 때 user 테이블의 last_login 필드가 갱신됨
        - db transaction의 수를 크게 증가시킬 수 있고, 이는 서버가 느려지는 원인이 됨
    - ALGORITHM
        - 토큰에 대한 서명/확인 작업을 수행하는 데 사용되는 PyJWT 라이브러리의 알고리즘
        - HMAC 설정 시, SIGNING_KEY 설정은 서명 / 확인에 모두 사용되고 VERIFYING_KEY 설정은 무시됨
        - RSA 설정 시, SIGNING_KEY는 RSA private key를 포함한 문자열로 설정, VERIFYING_KEY는 RSA public key를 포함한 문자열로 설정
    - SIGNING_KEY
        - 생성된 토큰에 서명하기 위해 사용되는 키
        - HMAC 옵션에서는 서명 프로토콜에 필요한 비트 수 이상의 랜덤한 문자열이어야 함
        - RSA 옵션에서는 2048 비트 이상의 RSA private key를 포함한 문자열이어야 함
        - SimpleJWT는 기본적으로 256 비트의 HMAC를 사용하기 때문에 기본 값은 django project의 SECRET_KEY
    - VERIFYING_KEY
        - 생성된 토큰을 검증할 때 사용되는 키
        - HMAC 옵션에서는 무시되고, 대신 SIGNING_KEY 값이 사용됨
        - RSA 옵션에서는 RSA public key를 포함한 문자열이어야 함
    - AUDIENCE
        - None 으로 설정 시 필드가 토큰에서 제외되고 유효성 검사가 되지 않음
    - ISSUER
        - None 으로 설정 시 필드가 토큰에서 제외되고 유효성 검사가 되지 않음