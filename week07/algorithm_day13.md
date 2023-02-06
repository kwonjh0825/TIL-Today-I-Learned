# 그래프 탐색 알고리즘

- 시작 정점에서 간선을 타고 이동할 수 있는 모든 정점을 찾는 알고리즘
- 깊이 우선 방식, 너비 우선 방식이 있음
- 깊이 우선 탐색(DFS): 스택 활용
- 너비 우선 탐색(BFS): 큐 활용

# DFS

- Depth-First Search(깊이 우선 탐색)
- 시작 정점으로부터 갈 수 있는 하위 정점까지 가장 깊게 탐색
- 더 이상 갈 곳이 없다면 마지막 갈림길로 돌아와서 다른 정점을 탐색하며 결국 모든 정점을 방문하는 순회 방법
- 미로 탈출과 비슷
- 각 정점을 방문했는지 여부를 판단하는 방문 체크 리스트 필요
- 특징
  - 모든 정점을 방문하는 데 유리
  - 경우의 수, 순열, 조합 문제에 많이 사용됨
  - BFS에 비해 코드 구현 용이
  - 모든 정점을 방문할 필요가 없거나, 최단 거리를 구하는 경우 BFS가 유리
- 동작 과정
  1. 현재 정점 방문처리
  2. 인접한 모든 정점 확인
  3. 방문하지 않은 인접 정점으로 이동

# 알고리즘 과제

```python
# pr01. 10769: 행복한지 슬픈지
string = input().split(':')

cnt_happy = 0
cnt_sad = 0

for s in string:
    if '-(' in s:
        cnt_sad += 1
    elif '-)' in s:
        cnt_happy += 1

if not cnt_happy and not cnt_sad:
    print('none')
elif cnt_happy > cnt_sad:
    print('happy')
elif cnt_happy < cnt_sad:
    print('sad')
else:
    print('unsure')
```

- 위 방식대로 : 를 기준으로 split 하여 문제를 풀었더니 통과되었다.
- -(, -) 문자 개수를 세어서 비교하여 알맞은 문자를 출력하도록 하였다.
- 코드 리뷰 시간에 다른 조원의 풀이 중 count를 사용한 코드가 인상적이었다. 나는 count를 잊고 있었던 것 같다.

```python
# pr02. 2455: 지능형 기차
max_client = 0
now = 0
for _ in range(4):
    a, b = map(int, input().split())
    now -= a
    now += b
    max_client = max(max_client, now)
print(max_client)
```

- 기차 내 승객을 각 역에서 세고, 이전의 최대 승객수와 현재 승객수를 비교하여 최대 승객수를 갱신하도록 코드를 작성햐였다.

```python
# pr03. 2606: 바이러스
n = int(input())
m = int(input())

graph = [[] for _ in range(n+1)]
visited = [False] * (n+1)

for _ in range(m):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)

def dfs(s):
    stack = [s]
    visited[s] = True
    while stack:
        current = stack.pop()

        for adj in graph[current]:
            if not visited[adj]:
                visited[adj] = True
                stack.append(adj)
dfs(1)

print(len([x for x in visited if x]) - 1)
```

- 이 문제는 dfs 알고리즘을 통해 문제를 해결하였다. dfs 알고리즘은 오늘 교재에서 사용된 코드를 사용하였다.
- 노드와 간선을 그래프 형식으로 저장하고, 1번 컴퓨터에서부터 dfs를 통해 간선으로 연결된 모든 노드를 탐색하였다.
- 방문한 노드들의 리스트의 길이를 구한 후 1번 컴퓨터를 제외한 길이를 출력하였다.

```python
# pr04. 4963: 섬의 개수
dx = [1, 1, 0, -1, -1, -1, 0, 1]
dy = [0, 1, 1, 1, 0, -1, -1, -1]
while True:
    w, h = map(int, input().split())
    if not w and not h:
        break
    
    ans = 0
    graph = []
    for _ in range(h):
        graph.append(list(map(int, input().split())))
    
    visited = [[False] * w for _ in range(h)]
    
    def dfs(x, y):
        visited[x][y] = True
        for i in range(8):
            nx = x + dx[i]
            ny = y + dy[i]
            if 0 <= nx < h and 0 <= ny < w:
                if graph[nx][ny] and not visited[nx][ny]:
                    dfs(nx, ny)
    
    for x in range(h):
        for y in range(w):
            if graph[x][y] and not visited[x][y]:
                dfs(x, y)
                ans += 1
    print(ans)
```

- 이 문제도 dfs를 활용하여 해결하였다. 이번에는 재귀형식을 활용한 dfs 알고리즘을 사용하였다.
- 이차원 리스트로 이루어진 지도에서 땅을 발견한다면 dfs 함수를 호출하여 가로, 세로, 대각선 방향의 연결된 땅들을 모두 탐색 한 후 방문 표시를 하고 카운트를 1 증가시켰다.
- 이러한 방식으로 모두 탐색한 후 카운트를 출력해 섬의 개수를 확인할 수 있다.