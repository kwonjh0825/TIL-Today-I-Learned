# Branch

## What is Branch?

- 독립적인 작업 흐름을 만들고 관리하는 것

## 명령

- branch 생성
    - `git branch (branch_name)`
- branch 이동
    - `git checkout (branch_name)`
    - `git switch (branch_name)`
- branch 생성 및 이동
    - `git checkout -b (branch_name)`
- branch 목록
    - `git branch`
- branch 삭제
    - `git branch -d (branch_name)`
- branch 병합
    - `git merge (branch_name)`
    >현재 branch(일반적으로 master)와 branch_name을 병합한다.

## Branch 상황

1. fast-forward
    - branch 생성된 이후 master에 변경 사항이 없는 상황
2. merge commit
    - 서로 다른 commit을 merge 하는 과정에서 다른 파일이 수정되어 있는 상황
    - git이 auto merging 진행, commmit도 발생됨
3. merge commit 충돌
    - 서로 다른 commmit 을 merge 하는 과정에서 같은 파일의 동일 부분이 수정되어 있는 상황
    - git 이 auto merging 진행 못함. 충돌 메시지 발생
    - 원하는 형태의 코드로 직접 수정하고 직접 commit 발생해야 함

## Git Flow

- Git을 활용하여 협업하는 흐름으로 branch를 활용하는 전략을 의미한다.
- 정해진 답이 있는 것은 아님
- Branch 전략
    - master branch 는 반드시 배포 가능한 상태여야 한다.
    - feature branch  는 각 기능의 의도를 알 수 있도록 작성한다.
    - commmit message 는 매우 중요하며, 명확하게 작성한다.
    - Pull Request 를 통해 협업을 진행한다.
    - 변경사항을 반영하고 싶다면, master branch 에 병합한다.
- 과정 예시
    1. Branch 생성
    2. 작업
    3. Commit
    4. github 으로 branch push
    5. Pull Request
    6. Review
    7. Merge

## GitHub Flow Model

- Shared Repository Model
    - 동일한 저장소를 공유하여 활용하는 방식
    - 과정
        1. 팀원 초대 및 저장소 clone
        2. branch 에서 작업, push
        3. Pull request 생성
        4. Review, merge
    - 병합 후 개발은  merge 된 branch 삭제 후, master branch 업데이트 후 위 과정 반복
- Fork & Pull Model
    - Repository 에 Collaborator에 등록되지 않은 상태에서 진행된다.
    - GitHub 기반의 오픈 소스 참여 과정에서 쓰이는 방식
    - 과정
        1. Fork, Clone
        2. 이후 commit, push, PR 은 Shared Repository Model 과 동일