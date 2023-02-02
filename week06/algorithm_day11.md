# 그래프

- 정점(vertex)와 이를 연결하는 간선(edge)들의 집합으로 이루어진 비선형 자료구조
- 그래프 관련 용어
  - 정점(vertex): 간선으로 연결되는 객체이며, 노드(node)라고 하기도 함
  - 간선(Edge): 정점 간의 관계(연결)를 표현하는 선을 의미
  - 경로(Path): 시작 정점부터 도착 정점까지 거치는 정점을 나열한 것
  - 인접(Adjacency): 두 개의 정점이 하나의 간선으로 직접 연결된 상태를 의미
  - 차수(Degree): 하나의 정점에 연결된 간선의 개수
- 무방향 그래프
  - 간선의 방향이 없는 가장 일반적인 그래프
  - 간선을 통해 양방향의 정점 이동 가능
  - 모든 정점의 차수의 합 = 간선수 x 2
- 방향 그래프
  - 간선의 방향이 있는 그래프
  - 간선이 가리키는 정점으로 이동 가능
  - 진출 차수/진입 차수로 나누어짐

# 그래프의 표현

- 인접 행렬
  - 두 정점을 연결하는 간선이 없다면 0, 있으면 1을 가지는 행렬로 표현
- 인접 리스트
  - 리스트를 통해 각 정점에 대한 인접 정점들을 순차적으로 표현하는 방식

# 알고리즘 과제

```python
# pr01. 1547: 공
M = int(input())
ball = {1: 1, 2: 0, 3: 0}

for _ in range(M):
    x, y = map(int, input().split())
    if ball[x] or ball[y]:
        ball[x], ball[y] = ball[y], ball[x]

print(sorted(ball.items(), key=lambda x: -x[1])[0][0])
```

- 이 문제는 컵 번호를 key로, 공의 여부를 value로 하는 dictionary 를 활용하여, 공을 가지고 있는 컵이 입력으로 들어오면 공의 여부를 변경하도록 하였다.
- 마지막에 value를 기준으로 dictionary를 내림차순으로 정렬하여 컵 번호를 출력하도록 하였다.

```python
# pr02. 5576: 콘테스트
w_score = sum(sorted([int(input()) for _ in range(10)], reverse=True)[:3])
k_score = sum(sorted([int(input()) for _ in range(10)], reverse=True)[:3])
print(w_score, k_score)
```

- 이 문제는 10개의 입력을 내림차순 정렬하여 최대값 3개를 더한 점수를 각각 출력하여 해결하였다.

```python
# pr03. 2846. 오르막길
N = int(input())
li = list(map(int, input().split()))
up_cnt = 0
up_start = 0
ans = [0]

for i in range(1, len(li)):
    if li[i-1] < li[i] and up_cnt == 1:
        pass
    elif li[i-1] < li[i] and up_cnt == 0:
        up_start = li[i-1]
        up_cnt = 1
    elif not li[i-1] < li[i] and up_cnt == 1:
        ans.append(li[i-1] - up_start)
        up_start = 0
        up_cnt = 0
    else:
        up_cnt = 0
        up_start = 0
if up_cnt:
    ans.append(li[-1] - up_start)
print(max(ans))
```

- 이 문제는 처음 생각했던 것보다 복잡했던 문제였다.
- 오르막길을 올라가는 중인지를 확인하는 up_cnt 변수, 오르막길의 시작 높이를 저장하는 up_start 변수를 활용하였다.
- 오르막길을 처음 만난다면 오르막길을 올라가는 중이고 오르막길의 시작 높이를 저장하도록 한다.
- 오르막길이 끝났다면 ans 리스트에 오르막길 길이를 저장한다.
- 마지막에 ans 리스트의 최대값을 출력하도록 하였다.

```python
# pr04. 1251: 단어 나누기
string = input().strip()
ans = []
for i in range(1, len(string)-1):
    for j in range(i+1, len(string)):
        a = string[:i]
        b = string[i:j]
        c = string[j:]
        a = a[::-1]
        b = b[::-1]
        c = c[::-1]
        ans.append(a+b+c)
print(sorted(ans)[0])
```

- 이 문제는 다른 방식이 있는지 많이 고민하다가, 완전 탐색으로 문제를 해결하였다.
- 완전탐색을 통해 가능한 모든 문자열의 조합을 ans에 저장하고, 이 중 사전 순 가장 빠른 것을 출력하여 해결하였다.