## Fixture

- django가 데이터베이스로 가져오는 방법을 알고 있는 데이터 모음
- django가 직접 만들기 때문에 데이터베이스 구조에 맞추어 작성되어 있음

## Dumpdata

- 데이터베이스의 모든 데이터 출력
- 여러 모델을 하나의 json 파일로 만들 수 있음
- `python manage.py dumpdata [app_name[.ModelName] [app_name[.ModelName] ...]] > filename.json`

## Loaddata

- fixture data를 데이터베이스로 불러오기
- 기본 경로: app_name/fixtures
- django는 설치된 모든 app의 디렉토리에서 fixtures 폴더 이후의 경로로 fixtures 파일을 찾아 load
- `python manage.py loaddata filename.json ...`