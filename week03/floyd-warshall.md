# 플루이드 워셜 알고리즘

- 모든 노드에서 다른 모든 노드까지의 최단 경로를 모두 계산
- Dijkstra 알고리즘과 마찬가지로 단계별로 거쳐 가는 노드를 기준으로 알고리즘 수행, 다만 매 단계마다 방문하지 않은 노드 중 최단 거리를 갖는 노드를 찾는 과정이 필요하지 않음
- 3중 반복문을 통해 2차원 테이블에 최단 거리 정보를 저장
- 다이나믹 프로그래밍 유형에 속함
- 시간복잡도 : $O(N^3)$
- 과정
  - 각 단계마다 특정 노드 k를 거쳐 가는 경우를 확인
  - a에서 b 로 가는 최단 거리보다 a에서 k를 거쳐 b로 가는 거리가 더 짧은지 검사
  - 점화식 : $D_{ab} = min(D_{ab}, D_{ak} + D_{kb})$
- Python 구현 코드
  
    ```python
    INF = int(1e9)
    n = int(input())
    m = int(input())
    
    graph = [[INF] * (n+1) for _ in range(n+1)]
    
    # 자기 자신으로 가는 비용은 0
    for a in range(1, n+1):
    	for b in range(1, n+1):
    		if a == b:
    			graph[a][b] = 0
    # 간선에 대한 정보를 입력받아 그 값으로 초기화
    for _ in range(m):
    	a, b, c = map(int, input().split())
    	# a에서 b로 가는 비용 c
    	graph[a][b] = c
    		
    for k in range(1, n+1):
    	for a in range(1, n+1):
    		for b in range(1, n+1):
    			graph[a][b] = min(graph[a][b], graph[a][k] + graph[k][b])
    
    # 수행 결과 출력
    for a in range(1, n+1):
    	for b in range(1, n+1):
    		if graph[a][b] == INF:
    			print('INFINITY', end=' ')
    		else:
    			print(graph[a][b], end=' ')
    	print()
    ```
