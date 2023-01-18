# 벨만 포드 알고리즘

- 음의 간선이 포함된 상황에서도 사용할 수 있음.
- 음수 간선의 순환을 감지할 수 있음.
- 시간복잡도는 $O(VE)$로 Dijkstra 알고리즘에 비해 느리다.
- 동작 과정
    1. 출발 노드 설정
    2. 최단 거리 테이블 초기화
    3. 다음의 과정을 N-1번 반복
        - 전체 간선 E개를 하나씩 확인
        - 각 간선을 거쳐 다른 노드로 가는 비용을 계산하여 최단 거리 테이블을 갱신
- 음수 간선 순환이 발생하는지 체크 하고 싶다면 3번의 과정을 한번 더 수행하였을 때 최단 거리 테이블이 갱신되는지 확인. 갱신된다면 음수 간선 순환이 존재
- Python 구현 코드
  
    ```python
    import sys
    input = sys.stdin.readline()
    INF = int(1e9)
    
    def bf(start):
    	dist[start] = 0
    	for i in range(n):
    		for j in range(m):
    			cur = edges[j][0]
    			next_node = edges[j][1]
    			cost = edges[j][2]
    			if dist[cur] != INF and dist[next_node] > dist[cur] + cost:
    				dist[next_node] = dist[cur] + cost
    				# n 번째 라운드에서 값이 갱신되면 음수 순환 존재
    				if i == n-1:
    					return True
    	return False
    
    n, m = map(int, input().split())
    edges = []
    dist = [INF] * (n+1)
    
    for _ in range(m):
    	a, b, c = map(int, input().split())
    	# a 노드에서 b 노드로 가는 비용 c
    	edges.append((a, b, c))
    
    negative_cycle = bf(1)    # 1번 노드부터 시작
    
    if negative_cycle:
    	print('-1')
    else:
    	# 1번 노드를 제외한 다른 모든 노드로 가기 위한 최단 거리
    	for i in range(2, n+1):
    		if dist[i] == INF:
    			print('-1')
    		else:
    			print(dist[i])
    ```
