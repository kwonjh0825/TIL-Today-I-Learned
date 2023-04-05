## 회원가입

- User 객체를 create 하는 것

### UserCreationForm()

- 회원 가입을 위한 built-in ModelForm

### 회원가입 진행 후 에러 페이지

- 회원가입에 사용하는 UserCreationForm은 우리가 대체한 커스텀 유저 모델이 아닌 기존 유저 모델로 인해 작성된 클래스이기 때문에 에러 발생
- 커스텀 유저 모델을 사용하려면 UserCreationForm, UserChangeForm 두 가지를 다시 작성
- get_user_model()
    - 현재 프로젝트에서 활성화된 사용자 모델을 반환하는 함수

## 회원 탈퇴

- User 객체를 delete 하는 것
- `request.user.delete()`를 views.py 내 회원 탈퇴 함수에 작성

## 회원정보 수정

- User 객체를 update 하는 것

### UserChangeForm()

- 회원 정보 수정을 위한 built-in ModelForm
- 사용 시 문제점
    - 일반 사용자가 접근해서는 안될 정보들까지 모두 수정 가능해짐
- CustomUserChangeForm에서 접근 가능한 필드 설정

## 비밀번호 변경

- django는 비밀번호 변경 페이지를 회원정보 수정 form 에서 별도 주소로 안내(/accounts/password/)

### PasswordChangeForm()

- 비밀번호 변경을 위한 built-in Form

### update_session_auth_hash(request, user)

- 암호 변경 시 세션 무효화 방지
- 암호가 변경되어도 로그아웃 되지 않도록 새로운 password의 session data로 기존 session을 업데이트

## 로그인 사용자에 대한 접근 제한

- 로그인 사용자에 대해 접근을 제한하는 2가지 방법
    - is_authenticated 속성
    - login_required 데코레이터

### is_authenticated

- 사용자가 인증 되었는지 여부를 알 수 있는 User model의 속성(attributes)
- 모든 User 인스턴스에 대해 항상 True인 읽기 전용 속성
- Anonymous 에 대해서는 항상 False

### login_required

- 인증된 사용자에 대해서만 view 함수를 실행시키는 데코레이터
- 로그인하지 않은 사용자의 경우 /accounts/login/ 주소로 redirect 