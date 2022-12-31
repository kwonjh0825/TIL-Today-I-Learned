# stack

- 입구와 출구가 같은 자료구조. 선입후출
- python에서의 예시
    - `stack.append(n)` : stack의 마지막에 n을 추가한다.
    - `stack.pop()` : stack에서 마지막 원소를 추출한다.

# Queue

- 입구와 출구가 모두 뚫려 있는 터널과 같은 자료구조. 선입선출
- 대기열을 구현할 때 사용
- python에서의 예시
    - `from collection import deque` 후 사용
    - 변수를 `deque()`로 선언
    - `queue.append(n)` : queue에 n을 삽입
    - `queue.popleft()` : queue에 먼저 들어온 원소를 추출한다.

# 완전 이진 트리

- 루트 노드부터 시작하여 왼쪽 자식 노드, 오른쪽 자식 노드 순서대로 데이터가 차례대로 삽입되는 트리

# Heap

- 완전 이진 트리 자료구조의 일종
- 힙에서는 항상 루트 노드를 제거
- 최소 힙(Min Heap)
    - 루트 노드가 가장 작은 값을 가짐
    - 값이 작은 데이터가 우선적으로 제거
    - Min-Heapify() : 최소 힙 구성 함수
    - 부모 노드로 거슬러 올라가며, 부모보다 자신의 값이 더 작은 경우에 위치를 교체
- 최대 힙(Max Heap)
    - 루트 노드가 가장 큰 값을 가짐
    - 값이 큰 데이터가 우선적으로 제거됨
- 힙에 새로운 원소가 삽입될 때
    - 새로운 원소가 삽입되었을 때 O(logN)의 시간 복잡도로 힙 성질을 유지하도록 할 수 있음
- 힙에서 원소가 제거될 때
    - 원소가 제거되었을 때 O(logN)의 시간 복잡도로 힙 성질을 유지할 수 있음
    - 원소를 제거할 때는 가장 마지막 노드가 루트 노드의 위치에 오도록 함
    - 이후 루트 노드에서부터 하향식으로(더 작은 자식 노드로) Heapify() 진행
- Python에서는 heapq 라이브러리 제공(Min-heap 방식 동작이 기본)
    - `heappush(h, value)` : h 리스트에  value 삽입
    - `result.append(heapq.heappop(h))` 를 통해 힙에 삽입된 모든 원소를 차례대로 꺼내어 담음. 오름차순으로  정렬됨

# 우선순위 큐

- 우선순위가 가장 높은 데이터를 가장 먼저 삭제하는 자료구조
- 우선 순위에 따라 데이터를 처리하고 싶을 때 사용
- 구현 방법
    - 리스트를 이용하여 구현
    - 힙을 이용하여 구현
- N 개의 데이터를 힙에 넣었다가 모두 꺼내는 작업은 정렬과 동일(힙 정렬). 시간복잡도 O(NlogN)

# 트리

- 가계도와 같은 계층적인 구조를 표현할 때 사용할 수 있는 자료구조
- 용어
    - 루트 노드(root node) : 부모가 없는 최상위 노드
    - 단말 노드(leaf node) : 자식이 없는 노드
    - 크기(size) : 트리에 포함된 모든 노드의 개수
    - 깊이(depth) : 루트 노드로부터의 거리
    - 높이(height) : 깊이 중 최댓값
    - 차수(degree) : 각 노드의 (자식 방향) 간선 개수
- 트리의 크기가 N이라면, 전체 간선의 개수는 N-1 이다.
- 트리의 순회
    - 전위 순회(preorder traverse) : 루트 → 왼쪽 자식노드 → 오른쪽 자식 노드
    - 중위 순회(inorder traverse) :  왼쪽 자식노드 → 루트 → 오른쪽 자식 노드
    - 후위 순회(postorder traverse) : 왼쪽 자식노드 → 오른쪽 자식 노드 → 루트
- Python에서 Tree 구현
    
    ```python
    class Node: 
    	def __init__(self, data, left_node, right_node):
    		self.data = data
    		self.left_node = left_node
    		self.right_node = right_node
    ```
    
- Tree 순회 구현(ex. 전위 순
    
    ```python
    def preorder(node): 
    	print(node.data, end=' ')   # 루트
    	if node.left_node != None:  # 왼쪽 
    		pre_order(tree[node.left_node])
    	if node.right_node != None: # 오른쪽
    		pre_order(tree[node.right_node])
    ```
    

# 이진 탐색 트리(Binary Search Tree)

- 이진 탐색이 동작할 수 있도록 고안된 효율적인 탐색이 가능한 자료구조
- 이진 탐색 트리의 특징 : 왼쪽 자식 노드 < 부모 노드 < 오른쪽 자식 노드

# 이진 인덱스 트리(Binary Index Tree)

- 이진법 인덱스 구조를 활용해 구간 합 문제를 효과적으로 해결해 줄 수 있는 자료구조
- 펜윅 트리(Fenwick tree)라고도 함
- 0이 아닌 마지막 비트를 찾는 법
    - 특정 숫자 K의 0이 아닌 마지막 비트를 찾기 위해 K & -K 계산
- 트리 구조 만들기
    - 0이 아닌 마지막 비트 : 내가 저장하고 있는 값들의 개수
- 특정 값을 변경할 때(Update)
    - 0이 아닌 마지막 비트만큼 더하면서 구간들의 값을 변경
- 1부터 N 까지의 합(누적 합) 구하기
    - 0이 아닌 마지막 비트만큼 빼면서 구간들의 값의 합 계산
- Python 구현
    
    ```python
    # i번째 수까지의 누적 합을 계산하는 함수
    def prefix_sum(i):
    	result = 0
    	while i > 0:
    		result += tree[i]
    		# 0이 아닌 마지막 비트만큼 빼가면서 이동
    		i -= (i & -i)
    	return result
    
    # i번째 수를 dif 만큼 더하는 함수
    def update(i, dif):
    	while i <= n:
    		tree[i] += dif
    		# 0이 아닌 마지막 비트만큼 더하면서 이동
    		i += (i & -i)
    
    # start부터 end 까지의 구간 합을 계산하는 함수
    def inteval_sum(start, end):
    	return prefix_sum(end) - prefix_sum(start - 1)
    
    # update 연산인 경우
    update(b, c - arr[b]) # 바뀐 크기(dif) 만큼 적용
    arr[b] = c
    ```