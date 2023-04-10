## static file 제공

- 경로에 따른 Static file 제공하기
    - 기본 경로: `app/static/`
    - 추가 경로: `STATICFILES_DIRS`

### 기본 경로 static file 제공

- 기본 경로에 이미지 파일 배치
- static 태그를 사용해 이미지 파일에 대한 url 제공

### STATIC_URL

- 기본 경로 및 추가 경로에 위치한 정적 파일을 참조하기 위한 URL
- 실제 파일, 디렉토리가 아니며 URL로만 존재
- 비어있지 않은 값으로 설정한다면 반드시 `/` 로 끝나야 함
- URL + STATIC_URL + 정적파일 경로

### 추가 경로 static file 제공

- 추가 경로에 이미지 파일 배치
- static 태그를 사용해 이미지 파일에 대한 url 제공

## Media files

- 사용자가 웹에서 업로드하는 정적 파일

### ImageField()

- 이미지 업로드에 사용하는 모델 필드
- 이미지 객체가 직접 저장되는 것이 아닌 이미지 파일의 경로 문자열이 db에 저장

### 미디어 파일을 제공하기 전 준비

- settings.py에 MEDIA_ROOT, MEDIA_URL 설정
- 작성한 MEDIA_ROOT, MEDIA_URL에 대한 url 지정
- MEDIA_ROOT: 미디어 파일들이 위치하는 디렉토리의 절대 경로
- MEDIA_URL: MEDIA_ROOT에서 제공되는 미디어 파일에 대한 주소 생성(STATIC_URL과 동일한 역할)
- urls.py 파일에 urlpatterns에 `static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)` 추가
- Pillow 라이브러리 설치

### 업로드 이미지 제공

- url 속성을 통해 업로드 파일의 경로 값을 얻을 수 있음
- `article.image.url`: 업로드 파일 경로
- `article.image`: 업로드 파일의 이름 제공
