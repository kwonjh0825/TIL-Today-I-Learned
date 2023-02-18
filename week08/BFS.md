# BFS 알고리즘

- Breadth-First search(너비 우선 탐색)
- DFS와 달리 재귀적으로 동작하지 않는다
- 큐를 사용하여 구현
- Prim, Dijkstra 알고리즘과 유사
- 동작 과정
    1. 현재 정점 방문처리, 큐에 인접 노드들 저장
    2. 큐에서 인접 노드들을 꺼내 차례로 검사
    3. 방문하지 않은 노드에 방문

```python
def bfs(n):
    visited[n] = True
    que.append(graph[n])
    while que:
        temp = que.popleft()
        for t in temp:
            if not visited[t]:
                visited[t] = True
                que.append(graph[t])
```