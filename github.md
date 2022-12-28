# 원격 저장소 (Github)

## 원격 저장소

- 파일이 원격 저장소 서버에서 관리되며, 여러 사람이 함께 공유하기 위한 저장소

## 명령

- `Push`
    - 로컬 저장소의 버전을 원격 저장소로 보낸다.
- `Pull`
    - 원격 저장소의 버전을 로컬 저장소로 가져온다.

## 초기 원격 저장소 설정

- 로컬 저장소에 원격 저장소 정보 설정
    - `git remote add origin (url)`
- 원격 저장소 정보 확인
    - `git remote -v`
- 원격 저장소로 보내기
    - `git push origin master` → 로컬의 master 를 원격 저장소 origin 으로 보냄
- 원격 저장소에서 받아오기
    - `git pull origin master` → 원격 저장소 origin의 내용을 로컬의 master로 받아옴
- 원격 저장소에서 복제 하기
    - `git clone (url) → url` 의 원격 저장소 내용을 복제해 온다

## gitignore

- git에 업로드 하지 않아야 할 파일들
- .gitignore 파일에 관리하지 않을 파일 이름/폴더를 저장
- gitignore 에 주로 포함되는 파일
    - 개발 언어
        - python의 venv/, javascript의 node_modules/
    - 개발 환경
        - 운영체제
        - 텍스트 에디터, IDE
- [gitignore.io](http://gitignore.io) → gitignore 파일 생성해주는 사이트

> git 완벽 책 : [git book](https://git-scm.com/book/ko/v2)