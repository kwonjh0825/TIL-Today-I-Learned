# Git

## 기초 흐름

- Untracked : 파일의 변경 사항
- Staged : 버전으로 기록하기 위한 파일 변경사항 저장
- Committed : 커밋(버전) 기록됨.

## 기본 명령어
- add
    - working directory 상의 변경 내용을 staging area에 추가하기 위해 사용
    - untracked, modified 상태의 파일을 staged 상태로 변경
- commit
    - staged 상태의 파일들을 커밋을 통해 버전으로 기록
    - 커밋 메시지는 변경 사항을 나타낼 수 있도록 명확하게 작성해야 함
- log
    - 현재 저장소에 기록된 커밋 조회
    - -n : 최근 n개
    - --oneline : 한줄로
- status
    - git 저장소에 있는 파일의 상태를 확인할 때 사용

## 버전 관리

- 스냅샷으로 관리하고, 매우 크기가 작음
- 파일이 달라지지 않았다면 성능을 위해 파일을 새로 저장하지 않는 방식