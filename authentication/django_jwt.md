## JWT 구현 방법

- 로그인 시 access / refresh token 을 확인하도록 구현
- token 내에는 user의 pk 값(id)와 사용자명(username)을 포함하도록 설정

### urls.py

```python
from django.urls import path
from rest_framework_simplejwt.views import TokenRefreshView
from . import views

urlpatterns = [
		# token 확인
    path('token/', views.MyTokenObtainPairView.as_view(), name='my_token'),
		# token 새로고침
    path('token/refresh/', TokenRefreshView.as_view(), name='token_refresh'),
]
```

### views.py

```python
class MyTokenObtainPairView(TokenObtainPairView):
    serializer_class = MyTokenObtainPairSerializer
```