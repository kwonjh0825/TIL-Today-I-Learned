# 코딩테스트 모의고사 풀이

```python
# 1208. Flatten
for t in range(1, 11):
    dump = int(input())
    ground = list(map(int, input().split()))

    for _ in range(dump):
        max_h = max(ground)
        min_h = min(ground)
        
        if max_h - min_h < 2:
            break
        else:
            ground[ground.index(max_h)] -= 1
            ground[ground.index(min_h)] += 1
    print(f'#{t} {max(ground)-min(ground)}')
```

- 이 문제는 상자들을 평탄화하는 문제로 덤프 한번 당 가장 높이 쌓여있는 상자 중 하나를 가장 낮은 곳으로 옮기는 역할을 한다.
- 덤프를 주어진 횟수만큼 수행하되, 최고점과 최저점의 차이가 1 이하라면 남은 덤프 횟수에 관계없이 코드를 종료하도록 작성하였다.

```python
# 1949. 등산로 조성
T = int(input())
dx = [1, 0, -1, 0]
dy = [0, 1, 0, -1]

for t in range(1, T+1):
    N, K = map(int, input().split())
    ground = []
    max_h = 0
    max_route = 0
    visited = [[0] * N for _ in range(N)]

    for i in range(N):
        li = list(map(int, input().split()))
        max_h = max(max(li), max_h)
        ground.append(li)    

    def dfs(x, y, construct):
        global max_route, visited
        max_route = max(max_route, visited[x][y])
        for i in range(4):
            nx = x + dx[i]
            ny = y + dy[i]

            if 0 <= nx < N and 0 <= ny < N and not visited[nx][ny]:
                if ground[x][y] > ground[nx][ny]:
                    visited[nx][ny] = visited[x][y] + 1
                    dfs(nx, ny, construct)
                    visited[nx][ny] = 0
                elif ground[x][y] > ground[nx][ny] - K and not construct:
                    temp = ground[nx][ny]
                    ground[nx][ny] = ground[x][y] - 1
                    construct = True
                    visited[nx][ny] = visited[x][y] + 1
                    dfs(nx, ny, construct)
                    ground[nx][ny] = temp
                    construct = False
                    visited[nx][ny] = 0         

    for i in range(N):
        for j in range(N):
            if ground[i][j] == max_h:
                visited[i][j] = 1
                dfs(i, j, construct= False)
                visited[i][j] = 0
    print(f'#{t} {max_route}')
```

- 이때까지 강의시간에 푼 문제 중 가장 어려운 것 같았다. 단순한 dfs와 다르게 다른 과정이 같이 들어가 있기 때문인 것 같았다.
- 이번 문제에서 방문을 기록하는 visited 리스트는 처음엔 평소처럼 `False`, `True` 로 이루어지게 코드를 작성하였는데, 다른 길이를 저장할 방법이 딱히 떠오르지 않아(사실 다른 변수에 할당해봤지만 실패했다) 해당 루트의 길이를 저장(방문하지 않았다면 0을 저장)하도록 하였다.
- 이 문제에서는 한 노드에 대해서 dfs가 완료되면 그 이후 visited를 0으로 초기화 해줘야 한다. 그렇지 않으면 해당 노드는 계속 visited된 상태로 다른 노드에서 출발한 등산로를 탐색할 때 해당 노드를 방문할 수 없기 때문이다.
- 같은 이유로 만약 공사를 하여 높이를 깎게 된다면, 공사를 한 후 dfs가 완료되면 높이를 공사 이전으로 돌려줘야 한다.
- 등산로는 항상 가장 높이가 높은 곳에서부터 출발하기 때문에, 그래프를 순회할 때 가장 높이가 높은 곳에서만 dfs를 실행하도록 작성하였다.
- 다른 문제들은 그래도 금방 생각났는데, 이 문제만 거의 1시간 넘게 소비해서 힘들었던 것 같다.

```python
# 3499. 퍼펙트 셔플
T = int(input())

for t in range(1, T+1):
    N = int(input())
    li = list(input().split())
    li_left = list(reversed(li[:(N+1)//2]))
    li_right = list(reversed(li[(N+1)//2:]))
    print(f'#{t}', end=' ')
    for i in range(N):
        if i % 2:
            print(li_right.pop(), end=' ')
        else:
            print(li_left.pop(), end=' ')
    print()
```

- 이 문제는 입력받은 카드를 반으로 나눈 후 반으로 나뉜 카드 목록에서 한 장씩 꺼내 섞는 코드이다.
- 한 장은 왼쪽 절반 리스트에서, 다음 장은 오른쪽 절반 리스트에서 꺼내야 하기 때문에 0부터 n-1 까지 for 문을 순회하며 짝수 번째일 때 왼쪽, 홀수 번째일때 오른쪽 목록에서 카드를 꺼내도록 작성하였다.
- 카드를 꺼내는 것은 pop을 활용해야겠다는 생각이 들어 왼쪽 절반을 뒤집은 것과 오른쪽 절반을 뒤집은 것을 따로 저장 후 하나씩  pop 하였다.

```python
# 4406. 모음이 보이지 않는 사람
T = int(input())

for t in range(1, T+1):
    string = input()
    ans = ''
    for s in string:
        if s not in 'aeiou':
            ans += s
    print(f'#{t} {ans}')
```

- 이 문제는 입력받은 문자열 중 모음을 제외한 것을 출력하는 문제다.
- 빈 문자열을 선언한 후, 입력 문자열 중 모음을 제외한 것을 빈 문자열에 추가한 후 출력하도록 작성하였다.
- 이 문제가 오늘 문제 중에선 가장 쉬웠던 것 같다. 아마 단순 문자열을 다루는 문제여서 그런 것 같다.

```python
# 7465. 창용 마을 무리의 개수
T = int(input())

for t in range(1, T+1):
    N, M = map(int, input().split())
    graph = [[] for _ in range(N+1)]
    visited = [False] * (N+1)
    cnt = 0

    for _ in range(M):
        a, b = map(int, input().split())
        graph[a].append(b)
        graph[b].append(a)
    
    def dfs(a):
        visited[a] = True
        for i in graph[a]:
            if not visited[i]:
                dfs(i)
    
    for i in range(1, N+1):
        if not visited[i]:
            dfs(i)
            cnt += 1
    
    print(f'#{t} {cnt}')
```

- 이 문제는 서로 아는 관계이거나 몇 사람을 거쳐서 알 수 있는 관계라면 같은 무리라고 인식되는 문제이다.
- 사람을 노드, 서로를 알고 있는 두 사람을 간선이라고 생각하면 그래프로 표현할 수 있고, 같은 무리는 간선으로 연결된 노드들의 집합이라고 볼 수 있다.
- 위와 같이 생각한다면 dfs를 통해 dfs를 한 번 완료하면 한 무리를 탐색했다고 볼 수 있기 때문에 cnt를 1 추가하는 방식으로 코드를 작성하였다.

```python
# 11856. 반반
N = int(input())

for t in range(1, N+1):
    string = input()
    set_string = set(string)

    if len(set_string) == 2:
        for s in set_string:
            if string.count(s) != 2:
                print(f'#{t} No')
                break
        else:
            print(f'#{t} Yes')
    else:
        print(f'#{t} No')
```

- 이 문제는 4개의 영어 대문자로 이루어진 입력에 대하여 정확히 다른 두 가지의 문자가 두 번 등장하는지 판별하는 문제이다.
- 두 가지의 문자로 이루어져 있는지는 set을 통해 중복을 제거한 집합을 구성하고 길이를 통해 확인했다.
- 그 후 set의 원소들이 입력받은 문자열에 2번 이상 등장한다면 No를, 2번만 등장한다면 Yes 를 출력하도록 작성하였다.
- 사실 출력이 Yes 와 No 두 가지로 구성되어 있는데, 내가 작성한 코드는 출력하는 구문이 3가지라 별로 좋은 코드가 아닌 것 같다. 그런데 더 좋은 방법이 떠오르지 않아서 일단 저렇게 제출하였다.

# 모의고사 후기

- 이번 모의고사의 전체적인 난이도는 지난 번 모의고사보다 쉽게 느껴졌다. (한 문제 빼고)
- D3, D4 정도의 난이도라고 적혀 있었지만, set을 활용하는 문제나 단순 계산 문제들이 많아서 쉽게 느껴졌던 것 같다.
- 여러 문제들이 쉽게 느껴져서 마지막 문제로 등산로 조성을 봤는데, 앞의 문제들보다 훨씬 어렵게 느껴졌다.
- 등산로 조성 문제만 고민을 1시간 넘게 했던 것 같다. 하지만 어찌저찌 해서 풀긴 했다.
- 시간을 많이 쓰고 여러 가지 방법을 써서 풀었기 때문에 오래 걸린 문제는 오늘 수업이 끝나면 다시 코드를 보고 조금 더 효율적으로 작성하거나 아니면 처음부터 다시 작성해서 확실하게 알고리즘을 공부할 수 있도록 해야 할 것 같다.
