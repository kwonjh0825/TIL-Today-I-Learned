# DFS

- 깊이 우선 탐색(Depth-First Search)
- 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘
- 스택 자료구조 또는 재귀 함수를 이용한다
- 과정
    1. 탐색 시작 노드를 스택에 삽입하고 방문 처리
    2. 스택의 최상단 노드에 방문하지 않은 인접한 노드가 하나라도 있으면 그 노드를 스택에 넣고 방문 처리. 방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼냄
    3. 2번 과정을 수행할 수 없을 때까지 진행
- Python 에서 코드 작성
    
    ```python
    def dfs(graph, v, visited):
    	visited[v] = True
    	print(v, end=' ')
    	for i in graph[v]:
    		if not visited[i]:
    			dfs(graph, i, visited)
    ```
    

# BFS

- 너비 우선 탐색(Breadth-First Search)
- 그래프에서 가까운 노드부터 우선적으로 탐색하는 알고리즘
- 큐 자료구조를 이용
- 최단 경로 문제에 효과적으로 사용
- 과정
    1. 탐색 시작 노드를 큐에 삽입하고 방문처리
    2. 큐에서 노드를 꺼낸 뒤 해당 노드의 인접 노드 중 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리
    3. 더 이상 2번의 과정을 수행할 수 없을 때까지 반복
    
    ```python
    from collections import deque
    
    def bfs(graph, start, visited):
    	queue = deque([start])
    	visited[start] = True
    
    	while queue:
    		v = queue.popleft()
    		print(v, end=' ')
    		for i in graph[v]:
    			if not visited[i]:
    				queue.append(i)
    				visited[i] = True
    ```
    

# 예제 <음료수 얼려 먹기>

- N x M 크기의 얼음 틀이 있습니다. 구멍이 뚫려 있는 부분은 0, 칸막이가 존재하는 부분은 1로 표시됩니다. 구멍이 뚫려 있는 부분끼리 상, 하, 좌, 우로 붙어 있는 경우 서로 연결되어 있는 것으로 간주합니다. 이 때 얼음 틀의 모양이 주어졌을 때 생성되는 총 아이스크림의 개수를 구하는 프로그램을 작성하세요
- 첫 번째 줄에는 얼음 틀의 세로길이 N, 가로길이 M이 주어진다.
- 두 번째 줄부터는 N+1 번째 줄까지 얼음 틀의 형태가 주어진다.

## solution

- DFS 혹은 BFS 로 해결 가능
- DFS 활용 알고리즘
    1. 특정한 지점의 주변 상, 하, 좌, 우를 살펴본 뒤에 주변 지점 중에서 값이 0이면서 아직 방문하지 않은 지점이 있다면 해당 지점을 방문
    2. 방문한 지점에서 다시 상, 하, 좌, 우를 살펴보면서 방문을 진행하는 과정을 반복하면 연결된 모든 지점을 방문할 수 있음
    3. 모든 노드에 대해 1, 2 번의 과정을 반복. 방문하지 않은 지점의 수를 카운트
- python 정답 코드 (DFS)
    
    ```python
    def dfs(x, y) : 
    	if x <= -1 or x >= n or y <= -1 or y >= m:    # 범위를 벗어나면 종료
    		return False
    	if graph[x][y] == 0:
    		graph[x][y] = 1
    		dfs(x-1, y)
    		dfs(x, y-1)
    		dfs(x+1, y)
    		dfs(x, y+1)
    		return True
    	return False
    
    n, m = map(int, input().split())
    
    graph = []
    for i in range(n):
    	graph.append(list(map(int, input())))
    
    result = 0
    for i in range(n):
    	for j in range(m):
    		if dfs(i, j) == True:
    			result += 1
    print(result)
    ```
    

# 예제 <미로 탈출>

- N x M 크기의 직사각형 형태의 미로가 있다. 미로에는 여러 마리의 괴물이 있어 이를 피해 탈출해야 한다.
- 첫 번째 위치는 (1, 1) 이며 출구는 (N, M)의 위치에 존재하며 한 번에 한 칸씩 이동할 수 있습니다. 이때 괴물이 있는 부분은 0으로, 괴물이 없는 부분은 1로 표시되어 있습니다. 미로는 반드시 탈출할 수 있는 형태로 제시됩니다. 이때 탈출하기 위해 움직여야 하는 최소 칸의 개수를 구하세요. 칸을 셀 때는 시작 칸, 마지막 칸을 모두 포함해서 계산합니다.
- 첫째 줄에는 미로의 크기 N, M 이 주어진다.
- 다음 N개의 줄에는 각각 M 개의 정수(0, 1)로 미로의 정보가 주어진다. 시작 칸과 마지막 칸은 항상 1

## solution

- BFS 활용 알고리즘
    1. 처음에 (1, 1) 의 위치에서 시작
    2. (1, 1) 좌표에서 상, 하, 좌, 우로 탐색을 진행하면 바로 옆 노드인 (1, 2) 위치의 노드를 방문하고, 새롭게 방문하는 (1, 2) 노드의 값을 거리인 2로 바꾼다.
    3. 계속 BFS를 수행하면 최단 경로의 값들이 1씩 증가하는 형태로 변경됨
- python 정답 코드
    
    ```python
    from collections import deque
    
    def bfs(x, y):
    	queue = deque()
    	queue.append((x, y))
    	while queue:
    		x, y = queue.popleft()
    		for i in range(4):    # 네 가지 방향으로 위치 확인
    			nx = x + dx[i]
    			ny = y + dy[i]
    
    			if nx < 0 or nx >= n or ny < 0 or ny >= m:
    				continue
    			if graph[nx][ny] == 0:
    				continue
    			if graph[nx][ny] == 1:
    				graph[nx][ny] = graph[x][y] + 1
    				queue.append((nx, ny))
    	return graph[n-1][m-1]
    
    n, m = map(int, input().split())
    
    graph = []
    for i in range(n):
    	graph.append(list(map(int, input())))
    
    # 상하좌유 방향 정의
    dx = [-1, 1, 0, 0]
    dy = [0, 0, -1, 1]
    
    print(bfs(0, 0))
    ```