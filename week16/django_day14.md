## User 모델을 참조하는 2가지 방법

- `get_user_model()`
    - 반환 값: User Object(객체)
    - models.py 가 아닌 다른 모든 곳에서 참조할 때 사용
- `settings.AUTH_USER_MODEL`
    - 반환 값: accounts.User(문자열)
    - models.py 의 모델 필드에서 참조할 때 사용