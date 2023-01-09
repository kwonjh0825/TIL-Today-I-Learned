# 최단 경로 알고리즘

- 가장 짧은 경로를 찾는 알고리즘
- 다양한 문제 상황
    - 한 지점에서 다른 한 지점까지의 최단 경로
    - 한 지점에서 다른 모든 지점까지의 최단 경로
    - 모든 지점에서 다른 모든 지점까지의 최단 경로
- 그래프에서 각 지점은 노드, 지점 간 연결된 도로는 간선으로 표현

# Dijkstra 최단 경로 알고리즘

- 특정한 노드에서 출발하여 다른 모든 노드로 가는 최단 경로 계산
- 음의 간선이 없을 때 정상적으로 동작(현실 세계의 도로는 음의 간선으로 표현되지 않음)
- Greedy 알고리즘으로 분류됨(매 상황에서 가장 비용이 적은 노드를 선택해 임의의 과정 반복)
- 단계를 거치며 한 번 처리된 노드의 최단 거리는 고정되어 더 이상 바뀌지 않는다
    - 한 단계당 하나의 노드에 대한 최단 거리를 확실히 찾는 것
- 알고리즘을 수행한 뒤에 테이블에 각 노드까지의 최단 거리 정보가 저장된다.
- 동작 과정
    1. 출발 노드 설정
    2. 최단 거리 테이블 초기화
    3. 방문하지 않은 노드 중에서 최단 거리가 가장 짧은 노드를 선택
    4. 해당 노드를 거쳐 다른 노드로 가는 비용을 계산하여 최단 거리 테이블 갱신
    5. 위 과정에서 3~4번 반복
- 간단한 구현 방법
    - 매 단계마다 1차원 테이블의 모든 원소를 순차 탐색)
    
    ```python
    import sys
    input = sys.stdin.readline
    INF = int(1e9)
    
    n, m = map(int, input().split())   # 노드의 개수, 간선의 개수
    start = int(input())
    graph = [[] for i in range(n+1)]
    visited = [False] * (n + 1)
    distance = [INF] * (n + 1)
    
    # 간선 정보 입력받기
    for _ in range(m):
    	a, b, c = map(int, input().split())
    	graph[a].append((b, c))
    	# a번 노드에서 b번 노드로 가는 비용이 c
    
    # 방문하지 않은 노드 중에서 가장 최단 거리가 짧은 노드의 번호를 반환
    def get_smallest_node():
    	min_value = INF
    	index = 0
    	for i in range(1, n+1):
    		if distance[i] < min_value and not visited[i]:
    			min_value = distance[i]
    			index = i
    	return index
    
    def dijkstra(start):
    	# 시작 노드에 대해 초기화
    	distance[start] = 0
    	visited[start] = True
    	for j in graph[start]:
    		distance[j[0]] = j[1]
    	# 시작 노드를 제외한 전체 n-1 개 노드에 대해 반복
    	for i in range(n-1):
    		# 현재 최단 거리가 가장 짧은 노드를 꺼내 방문처리
    		now = get_smallest_node()
    		visited[now] = True
    		# 현재 노드와 연결된 다른 노드를 확인
    		for j in graph[now]:
    			cost = distance[now] + j[1]
    			# 현재 노드를 거쳐 다른 노드로 이동하는 거리가 더 짧은 경우 
    			if cost < distance[j[0]]:
    				distance[j[0]] = cost
    
    dijkstra(start)
    
    for i in range(1, n+1):
    	if distance[i] == INF:
    		print('infinity')
    	else:
    			print(distance[i])
    ```
    
    - 시간 복잡도 : $O(V^2)$, V : 노드의 개수
- 개선된 구현 방법
    - 단계마다 방문하지 않은 노드 중 최단 거리가 가장 짧은 노드를 선택하기 위해 Heap 자료구조 사용
    
    ```python
    import heapq
    import sys
    input = sys.stdin.readline
    INF = int(1e9)
    
    n, m = map(int, input().split())    # 노드, 간선의 개수
    start = int(input())
    graph = [[] for i in range(n+1)]
    distance = [INF] *(n+1)
    
    for _ in range(m):
    	a, b, c = map(int, input().split())
    	graph[a].append((b, c))
    	# a번 노드에서 b번 노드로 가는 비용이 c
    
    def dijkstra(start):
    	q = []
    	heapq.heappush(q, (0, start))
    	distance[start] = 0
    	while q:
    		dist, now = heapq.heappop(q)    # 최단 거리가 가장 짧은 노드 정보 꺼내기
    		if distance[now] < dist:
    			continue
    		for i in graph[now]:
    			cost = dist + i[1]
    			if cost < distance[i[0]]:
    				distance[i[0]] = cost
    				heapq.heappush(q, (cost, i[0]))
    
    dijkstra(start)
    
    for i in range(1, n+1):
    	if distance[i] == INF:
    		print('infinity')
    	else:
    		print(distance[i])
    ```
    
    - 시간 복잡도 : $O(E\log V)$, E : 간선, V :  노드