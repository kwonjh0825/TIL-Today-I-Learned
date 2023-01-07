# 정렬 알고리즘

- 정렬이란 데이터를 특정한 기준에 따라 순서대로 나열하는 것
- 문제 상황에 따라 적절한 정렬 알고리즘이 공식처럼 사용됨

# 선택 정렬

- 처리되지 않은 데이터 중에서 가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸는 정렬 방식
- python 으로 작성된 코드
    
    ```python
    for i in range(len(array)):
    	min_idx = i
    	for j in range(i+1, len(array)):
    		if array[min_idx] > array[j]:
    			min_idx = j
    	array[i], array[min_idx] = array[min_idx], array[i]
    ```
    
- 시간 복잡도 → $O(N^2)$

# 삽입 정렬

- 처리되지 않은 데이터를 하나씩 골라 적절한 위치에 삽입한다
- 구현 방법은 선택 정렬보다 복잡하지만 일반적으로 더 효율적이다.
- python 으로 작성된 코드
    
    ```python
    for i in range(1, len(array)):
    	for j in range(i, 0, -1):
    		if array[j] < array[j-1]:
    			array, array[j-1] = array[j-1] , array[j]
    		else:
    			break
    ```
    
- 시간 복잡도
    - 최악의 경우 $O(N^2)$
    - 현재 리스트가 거의 정렬되어 있다면 매우 빠르게 동작
    - 최선의 경우 $O(N)$의 시간 복잡도를 가짐

# 퀵 정렬

- 기준 데이터를 설정하고, 그 기준보다 큰 데이터와 작은 데이터의 위치를 바꾸는 방법
- 일반적인 상황에서 가장 많이 사용되는 정렬 알고리즘 중 하나
- 기본적인 퀵 정렬은 첫 번째 데이터를 기준 데이터(Pivot)으로 설정
- 시간 복잡도 : 평균의 경우 $O(N\log N)$, 최악의 경우 $O(N^2)$를 가짐
- python 으로 작성된 코드(1)
    
    ```python
    def quicksort(array, start, end):
    	if start >= end:     # 원소가 1개이면 종료
    		return 
    	pivot = start        # 피벗은 첫번째 원소
    	left = start + 1
    	right = end
    	while(left <= right):
    		# 피벗보다 큰 데이터를 찾을 때까지 반복	
    		while(left <= end and array[left] <= array[pivot]):
    			left += 1
    		# 피벗보다 작은 데이터를 찾을 때까지 반복
    		while(right > start) and array[right] >= array[pivot]):
    			right -= 1
    		if(left > right):  # 엇갈렸다면 작은 데이터와 피벗을 교체
    			array[right], array[pivot] = array[pivot], array[right]
    		else:              # 엇갈리지 않았다면 작은 데이터와 큰 데이터 교체
    			array[left], array[right] = array[right], array[left]
    	# 분할 후 왼쪽, 오른쪽 부분에서 각각 정렬 수행
    	quicksort(array, start, right - 1)
    	quicksort(array, right + 1, end)
    ```
    
- python 으로 작성된 코드(2)
    
    ```python
    def quicksort(array):
    	if len(array) <= 1:    # 리스트가 하나 이하의 원소를 담고 있다면 종료
    		return array
    	pivot = array[0].      # 피벗은 첫 번째 원소
    	tail = array[1:]       # 피벗을 제외한 리스트
    	
    	left_side = [x for x in tail if x <= pivot]    # 분할된 왼쪽 부분
    	right_side = [x for x in tail if x > pivot]    # 분할된 오른쪽 부분
    
    	# 분할 이후 왼쪽, 오른쪽 부분에서 각각 정렬 수행, 이후 전체 리스트 반환
    	return quicksort(left_side) + [pivot] + quicksort(right_side)
    ```
    

# 계수 정렬

- 특정한 조건이 부합할 때만 사용할 수 있지만, 매우 빠르게 동작하는 정렬 알고리즘
- 데이터의 크기 범위가 제한되어 정수 형태로 표현할 수 있을 때 사용 가능
- 데이터의 개수 N, 데이터(양수) 중 최댓값이 K 일 때 최악의 경우 $O(N+K)$를 보장
- 과정
    1. 가장 작은 데이터부터 가장 큰 데이터까지의 범위가 모두 담길 수 있도록 리스트를 생성
    2. 데이터를 하나씩 확인하며 데이터의 값과 동일한 인덱스의 데이터를 1씩 증가 시킴
    3. 결과를 확인할 때는 리스트의 첫번재 데이터부터 하나씩 그 값만큼 반복하여 인덱스를 출력
- python 으로 작성된 코드
    
    ```python
    count = [0] * (max(array) + 1)
    
    for i in range(len(array)):
    	count[array[i]] += 1
    
    for i in range(len(count)):
    	for j in range(count[i]):
    		print(j, end=' ')
    ```