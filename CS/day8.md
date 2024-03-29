## 임계 영역

- 둘 이상의 스레드가 동시에 접근할 수 없도록 보장해야 하는 영역

### 임계 영역 문제 해결을 위한 3가지 조건

- 상호 배제(Mutual Exclusion)
  - 하나의 프로세스가 임계 영역에 있다면 다른 프로세스는 들어갈 수 없음
- 진행(Progress)
  - 임계 영역에 들어간 프로세스가 없는 상태에서 들어가려는 프로세스가 여러 개라면 어느 것이 들어갈 지 결정해야 함
- 한정 대기(Bounded Waiting)
  - 다른 프로세스의 starvation을 방지하기 위해, 한 번 임계구역에 들어간 프로세스는 다음 번 임계 영역에 들어갈 때 제한 필요

## 동기화 방식

- 임계 영역 문제가 발생하지 않도록 데이터를 한 번에 하나의 프로세스만 접근할 수 있도록 제한을 두는 방식

### 동기화 도구

- 뮤텍스(Mutex)
  - 공유 불가능한 자원의 동시 사용을 피하기 위해 사용하는 알고리즘
  - 임계구역을 가진 스레드들의 실행 시간이 서로 겹치지 않고 각각 단독으로 실행되도록 하는 기술(상호배제)
  - 한 프로세스에 의해 소유될 수 있는 key를 기반으로 한 상호 배제 기법
  - key에 해당하는 어떤 객체가 있으며, 이 객체를 소유한 스레드 또는 프로세스만 공유자원에 접근 가능
  - 다중 프로세스들의 공유 리소스에 대한 접근을 조율하기 위해 동기화 또는 락 사용
- 세마포어(Semaphore)
  - 멀티 프로그래밍 환경에서 공유된 자원에 대한 접근을 제한하는 방법
  - 공유 자원에 접근할 수 있는 프로세스의 최대 허용치만큼 동시에 사용자가 접근할 수 있음
  - 각 프로세스는 세마포어의 값을 확인하고 변경 가능
  - 자원을 사용하지 않는 상태가 될 때, 대기하던 프로세스가 즉시 자원을 사용
  - 이미 다른 프로세스에 의해 사용중이라는 사실을 알게 되면, 재시도 전에 일정 시간 대기
  - 세마포어를 사용하는 프로세스는 그 값을 확인하고, 자원을 사용하는 동안에는 그 값을 변경함으로써 다른 세마포어 사용자들이 대기하도록 해야 함
  - 세마포어는 이진수를 사용하거나 추가적인 값을 가질 수 있음
  - P연산, V연산으로만 접근할 수 있음
    - P연산
      
      ```python
        procedure P(S)        # 최초 s값은 1
        while S=0 do wait.    # s가 0이라면 1이 될때까지 기다리기
        S := S - 1            # s를 0으로 만들어 다른 프로세스가 들어오지 못하도록 함
        end P
      ```
            
    - V연산
            
      ```python
      procedure V(S)        # 현재 상태는 S가 0
      S := S + 1            # S를 1로 원위치시켜 해제하는 과정
      end V                 # 이제 다른 프로세스가 들어올 수 있음
      ```
            

### 뮤텍스와 세마포아의 차이

- 뮤텍스는 동기화 대상이 1개일 때 사용 가능, 세마포어는 동기화 대상이 1개 이상일 떄 가능
- 뮤텍스는 자원을 소유할 수 있고 책임을 가짐, 세마포어는 자원 소유 불가
- 뮤텍스는 소유하고 있는 스레드만이 뮤텍스 해제 가능, 세마포어는 소유하지 않는 스레드가 세마포어 해제 가능

## 스핀 락

- 임계 구역에 진입이 불가능할 때 진입이 가능할 때까지 루프를 돌면서 재시도하는 방식으로 구현된 락
- 임계 구역 진입 전까지 루프를 돌기 때문에 busy waiting이 발생, 이 때문에 CPU를 낭비할 수 있음
- context switching 이 발생하지 않아 CPU 부하를 줄일 수 있음
- 임계 영역이 짧거나 빠른 처리가 가능한 경우 효율적