# Django project, app

## django project

- 애플리케이션의 집합
- DB 설정, URL 연결, 전체 앱 설정 등을 처리

## django application

- 독립적으로 작동하는 기능 단위 모듈
- 각자 특정 기능을 담당하며 다른 앱들과 함께 하나의 프로젝트를 구성
- 앱 생성
    - `python manage.py startapp appname`
- 앱 등록
    - 프로젝트 디렉터리 아래 settings.py 파일 내 `INSTALLED_APPS`에 앱 이름 추가
- INSTALLED APP 등록 권장 순서
    1. local app
    2. third party app (설치를 통해 추가하는 앱)
    3. 기본 django app

# Django 디자인 패턴

## 소프트웨어 디자인 패턴

- 소프트웨어 설계에서 발생하는 문제를 해결하기 위한 일반적인 해결책
- 공통적 문제를 해결하는 데 쓰이는 형식화 된 관행

## MVC 디자인 패턴

- Model(데이터베이스) - View(사용자 인터페이스) - Controller(비즈니스 로직)
- 애플리케이션을 구조화하는 대표적인 패턴
- 시각적 요소와 뒤에서 실행되는 로직을 서로 영향 없이 독립적이고 쉽게 유지보수 할 수 있는 애플리케이션을 만들기 위해 도입

## MTV 디자인 패턴

- Model - Template - View
- django에서 애플리케이션을 구조화하는 패턴
- 기존 MVC 패턴과 동일하지만 명칭을 다르게 정의

## Django 프로젝트 구조

- settings.py
    - 프로젝트의 모든 설정 관리
- urls.py
    - URL과 이에 해당하는 적절한 views를 연결
- __init__.py
    - 해당 폴더를 패키지로 인식하도록 설정
- asgi.py
    - 비동기식 웹 서버와의 연결 관련 설정
- wsgi.py
    - 웹 서버와의 연결 관련 설정
- manage.py
    - Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인 유틸리티

## 앱 구조

- admin.py
    - 관리자용 페이지 설정
- models.py
    - DB와 관련된 Model 정의
    - MTV 패턴의 M
- views.py
    - HTTP요청을 처리하고 해당 요청에 대한 응답을 반환(url, mode, template 와 연계)
    - MTV 패턴의 V
- apps.py
    - 앱의 정보가 작성된 곳
- test.py
    - 프로젝트 테스트 코드를 작성하는 곳

## Templates

- 앱 폴더 안에 templates 폴더 작성
- templates 폴더 안에 템플릿 페이지 작성
- django 에서 template 를 인식하는 경로
    - app 폴더 / templates 까지 기본 경로로 인식

## 데이터 흐름에 따른 코드 작성

- URLs → View → Templates 순으로 작성 권장

## django html 내 이미지 삽입

- html 작성 시 경로를 일반 html 실습처럼 하면 이미지가 보이지 않는다.
- 이미지를 넣을 때 static 폴더를 따로 설정하고 경로 지정 필요
- settings.py
    - `import os` 추가
    - `STATIC_URL = /static/` 아래에 아래 코드 추가
        
        ```python
        STATICFILES_DIRS=[
            os.path.join(BASE_DIR,'myprofile','static')]
            
        STATIC_ROOT = os.path.join(BASE_DIR, 'static')
        ```
        
- urls.py
    - import 추가
        
        ```python
        from django.conf.urls.static import static
        from django.conf import settings
        ```
        
    - 아래와 같은 코드 추가
        
        ```python
        urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
        ```
        
- 이미지 파일을 static 폴더 안으로 옮김
- html 파일
    - 파일 맨 위에 `{%load static%}` 추가
    - 이미지 경로 지정 시 `{% static '이미지 경로' %}` 로 지정
        - static이 기본 경로