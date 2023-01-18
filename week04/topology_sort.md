# 위상 정렬

- 사이클이 없는 방향 그래프의 모든 노드를 방향성에 거스르지 않도록 순서대로 나열하는 알고리즘
- ex) 선수과목을 고려한 학습 순서
- 진입차수(Indegree): 특정한 노드로 들어오는 간선의 개수
- 진출차수(Outdegree): 특정한 노드에서 나가는 간선의 개수
- DAG(Direct Acyclic Graph, 순환하지 않는 방향 그래프)에서만 수행 가능
- 여러 가지의 답이 존재할 수 있다.
- 모든 원소를 방문하기 전 큐가 빈다면, 사이클이 존재한다고 판단할 수 있다.
- 큐, 스택을 통해 구현 가능
- 큐를 이용한 위상 정렬동작 과정
  1. 진입 차수가 0인 모든 노드를 큐에 넣는다.
  2. 큐가 빌 때까지 다음의 과정을 반복한다.
    1. 큐에서 원소를 꺼내 해당 노드에서 나가는 간선을 그래프에서 제거한다.
    2. 새롭게 진입차수가 0이 된 노드를 큐에 넣는다.
- Python 구현 코드

    ```python
    from collections import deque
    
    v, e = map(int, input().split())
    indegree = [0] * (v+1)
    
    graph = [[] for i in range(v+1)]
    
    for _ in range(e):
    	a, b = map(int, input().split())
    	graph[a].append(b)    # 정점 A에서 B로 이동 가능
    	indegree[b] += 1
    
    def topology_sort():
    	result = []
    	q = deque()
    
    	for i in range(1, v+1):
    		if indegree[i] == 0:
    			q.append(i)
    
    	while q:
    		now = q.popleft()
    		result.append(now)
    		for i in graph[now]:
    			indegree[i] -= 1
    			if indegree[i] == 0:
    				q.append(i)
    	for i in result:
    		print(i, end=' ')
    ```
    