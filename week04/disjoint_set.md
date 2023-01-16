# 서로소 집합 자료구조

- 서로소 집합이란 공통 원소가 없는 두 집합을 의미
- 서로소 부분 집합들로 나누어진 원소들의 데이터를 처리하기 위한 자료구조
- 두 종류의 연산 지원
  - 합집합 → 두 개의 원소가 포함된 집합을 하나의 집합으로 합치는 연산
  - 찾기 → 특정한 원소가 속한 집합이 어떤 집합인지 알려주는 연산
- 서로소 집합 자료구조는 합치기 찾기 자료구조(Union Find) 라고 불리기도 함.
- 기본적인 형태의 서로소 집합 자료구조에서는 루트 노드에 즉시 접근할 수 없음
- 동작 과정
    1. 합집합 연산을 확인하여 서로 연결된 두 노드  A, B 확인
        - A와 B의 루트 노드  A’, B’를 찾음
        - A’를 B’의 부모 노드로 설정
    2. 모든 합집합 연산을 처리할 때까지 1번의 과정 반복
- Python 구현 코드

    ```python
    def find_parent(parent, x):    # 특정 원소가 속한 집합을 찾기
    	# 루트 노드를 찾을 때까지 재귀
    	if parent[x] != x:
    		return find_parent(parent, parent[x])
    	return x
    
    def union_parent(parent, a, b):    # 두 원소가 속한 집합 합치기
    	a = find_parent(parent, a)
    	b = find_parent(parent, b)
    	if a < b:
    		parent[b] = a
    	else:
    		parent[a] = b
    
    v, e = map(int, input().split())
    
    for i in range(1, v+1):
    	parent[i] = i
    
    for i in range(e):
    	a, b = map(int, input().split())
    	union_parent(parent, a, b)
    
    print('각 원소가 속한 집합: ', end=' ')
    for i in range(1, v+1):
    	print(find_parent(parent, i), end=' ')
    print()
    
    print('부모 테이블: ', end=' ')
    for i in range(1, v+1):
    	print(parent[i], end=' ')
    ```

- 합집합 편향이 이루어지는 경우 찾기 함수가 비효율적으로 동작(최악의 경우 $O(V)$로 동작)
- 찾기 함수를 최적화하기 위해 경로 압축 이용
  - 찾기 함수를 재귀적으로 호출한 뒤 부모 테이블 값을 바로 갱신
        
        ```python
        def find_parent(parent, x):
        	if parent[x] != x:
        		parent[x] = find_parent(parent, aprent[x])
        	return parent[x]
        ```
        
  - 경로 압축을 적용하면 각 노드에 대하여 찾기 함수를 호출한 이후 해당 노드의 루트가 바로 부모 노드가 됨. 시간 복잡도 개선.

# 무방향 그래프 내에서 사이클 판별

- 서로소 집합은 무방향 그래프 내에서의 사이클을 판별할 때 사용할 수 있음
- 동작 과정
    1. 각 간선을 하났기 확인하며 두 노드의 루트 노드를 확인
        - 루트 노드가 서로 다르다면 두 노드에 대하여 합집합 수행
        - 루트 노드가 서로 같다면 사이클 발생
    2. 그래프에 포함된 모든 간선에 대하여 1번 과정 반복
- Python 구현 코드

    ```python
    def find_parent(parent, x):
    	if parent[x] != x:
    		parent[x] = find_parent(parent, aprent[x])
    	return parent[x]
    
    def union_parent(parent, a, b):    
    	a = find_parent(parent, a)
    	b = find_parent(parent, b)
    	if a < b:
    		parent[b] = a
    	else:
    		parent[a] = b
    
    v, e = map(int, input().split())
    parent = [0] * (v+1)
    
    for i in range(1, v+1):
    	parent[i] = i
    
    cycle = False
    
    for i in range(e):
    	a, b = map(int, input().split())
    	# 사이클 발생 시 종료
    	if find_parent(parent, a) == find_parent(parent, b):
    		cycle = True
    	else:
    		# 사이클 발생하지 않았다면 합집합 수행
    		union_parent(parent, a, b)
    if cycle:
    	print('사이클 발생')
    else:
    	print('사이클 발생하지 않음')
    ```
