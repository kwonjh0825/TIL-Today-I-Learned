# 파일로부터 읽고 쓰기

- 파일 작업 시 일반적인 업무 순서
  1. file 핸들러 개체 생성
  2. file 핸들러를 이용하여 읽거나 쓰기 작업
  3. file 핸들러를 닫음
- 파일 읽기
  - readline()을 통해 한 줄씩 읽기 가능
  - readlines() 를 통해 모든 줄 읽기 가능
- 파일 쓰기
  - write()를 통해 문자열을 입력하여 파일에 쓰기 가능
  - writelines()를 통해 리스트를 파일에 쓰기 가능
- 파일 처리 모드
  - `r`: 읽기 전용
  - `w`: 쓰기 전용(기존 내용 삭제됨)
  - `a`: 파일 끝에 추가
  - `r+`: 읽고 쓰기 모드
  - `w+`: 읽고 쓰기 모드(기존 내용 삭제)
  - `a+`: 읽고 쓰기 모드(추가모드)
- pickle
  - pickling: 객체가 저장되기 위해 바이트 스트링으로 변환되는 과정(object serialization)
  - unpickling: 바이트 스트링에서 원본 객체로 복원되는 과정(object deserialization)
- pickle 모듈
  - `dump`: 데이터 저장
  - `load`: 데이터 읽기