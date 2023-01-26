# 스택(Stack)

- 쌓는다는 의미
- 데이터를 한쪽에서만 넣고 빼는 자료구조
- LIFO(Last In First Out, 후입선출)
- 이전 작업을 기억할 때 사용될 수 있음
- python에서는 list에 append, pop을 활용한 형식으로 스택 구현 가능
- 괄호 매칭, 함수 호출(재귀호출), 백트리캥, DFS(깊이우선 탐색)에 활용

# 큐(Queue)

- 줄을 사는 것과 같은 자료구조
- 한쪽 끝에서 데이터를 넣고, 다른 한쪽에서만 데이터를 뺄 수 있는 자료구조
- FIFO(First In First Out, 선입선출)
- 프로세스 관리(데이터 버퍼), 클라이언트 / 서버 에서의 메세지 큐에서 사용될 수 있음
- 덱(deque, double-ended queue)
  - 양방향으로 삽입, 삭제가 가능한 큐

# 알고리즘 과제

```python
# pr01. 10101: 삼각형 외우기
a = int(input())
b = int(input())
c = int(input())

if a+b+c == 180:
    if a == b and b == c:
        print('Equilateral')
    elif a == b or b == c or c == a:
        print('Isosceles')
    else:
        print('Scalene')
else:
    print('Error')
```

- 이 문제는 세 각의 합이 180인지 먼저 구분하고, 그 안에서 각의 크기에 따라 삼각형을 분류하였다.
- 다른 조원의 풀이 중 삼각형을 분류할 때 set()을 통해 구분하는 방식이 인상적이었다.

```python
# pr02. 2720: 세탁소 사장 동혁
T = int(input())
for _ in range(T):
    cnt = []
    dollar = int(input())
    cnt.append(dollar//25)
    dollar = dollar % 25

    cnt.append(dollar//10)
    dollar = dollar % 10

    cnt.append(dollar//5)
    dollar = dollar % 5

    cnt.append(dollar)
    print(*cnt)
```

- 이 문제는 거스름돈 단위가 큰 것부터 작은 것 순으로 거슬러 줄 돈을 계산했다.

```python
# pr03. 1453: 피시방 알바
input()
li = list(map(int, input().split()))
now = []
cnt = 0
for l in li:
    if l not in now:
        now.append(l)
    else:
        cnt += 1
print(cnt)
```

- 이 문제는 새로운 리스트를 만들어 기존 리스트에 좌석에 앉은 손님이 존재한다면 1씩 카운트를 하도록 작성하였다.
- 이 문제 역시 set()을 통해 푼 조원이 있었는데, 입력으로 받은 리스트의 길이에서 set을 통해 중복을 제거한 길이를 빼 계산하는 방식이었다. 훨씬 간단하게 구현한 것 같아 인상적이었다.

```python
# pr04. 10773: 제로
import sys
input = sys.stdin.readline

k = int(input())
li = []
for _ in range(k):
    n = int(input())
    if n:
        li.append(n)
    else:
        li.pop()
print(sum(li))
```

- 이 문제는 문제에서 말하는 방법을 그대로 코드로 옮겼다. 0이 아닌 숫자가 들어온다면 배열에 추가하고, 0이 입력된다면 최근에 들어온 숫자를 지우도록 하였다.

```python
# pr05. 2161: 카드1
from collections import deque

n = int(input())
li = deque(x for x in range(1, n+1))
for _ in range(n):
    print(li.popleft())
    if li:
        li.append(li.popleft())
```

- 이 문제 역시 문제에서 말하는 방식을 그대로 코드로 옮긴 경우이다. 가장 위에 있는 카드를 버린 후, 제일 위의 카드를 제일 아래로 보내는 방식이다.

```python
# pr06. 9012: 괄호
T = int(input())
for _ in range(T):
    string = input()
    stack = []

    for s in string:
        if s == '(':
            stack.append(s)
        else:
            if stack:
                stack.pop()
            else:
                print('NO')
                break
    else:
        if not stack:
            print('YES')
        else:
            print('NO')
```

- 이 문제의 경우 소괄호만 입력으로 주어지기 때문에 간단한 방식으로 코드를 작성했다. 여는 소괄호가 들어오면 스택에 추가하고, 닫는 소괄호가 들어온 경우 스택에 여는 소괄호가 있는 경우 스택에서 하나를 제거하고 그렇지 않다면 괄호의 짝이 맞지 않아 no를 출력하도록 하였다.
- 모든 문자열에 대해 점검이 끝나고 스택이 비어 있다면 yes, 그렇지 않다면 no를 출력하도록 하였다.