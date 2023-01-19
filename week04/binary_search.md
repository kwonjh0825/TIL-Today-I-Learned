# 탐색 알고리즘

- 순차 탐색: 리스트 안에 있는 특정한 데이터를 찾기 위해 앞에서부터 데이터를 하나씩 확인하는 방법
- 이진 탐색: 정렬되어 있는 리스트에서 탐색 범위를 절반씩 좁혀가며 데이터를 탐색하는 방법
  - 탐색 시작점, 끝점, 중간점을 이용해 탐색 범위 설정
  - 시간 복잡도에서 순차 탐색보다 유리

# 이진 탐색

- Python 구현 코드(재귀함수 활용)
    
    ```python
    def binary_search(arr, target, start, end):
    	if start > end:
    		return None
    	mid = (start + end) // 2
    	
    	if arr[mid] == target:
    		return mid
    	elif arr[mid] > target:
    		return binary_search(arr, target, start, mid-1)
    	else:
    		return binary_search(arr, target, mid + 1, end)
    ```
    
- Python 구현 코드(반복문 활용)
    
    ```python
    def binary_search(arr, target, start, end):
    	while start <= end:
    		mid = (start + end) // 2
    		if arr[mid] == target:
    			return mid
    		elif arr[mid] > target:
    			end = end - 1
    		else:
    			start = mid + 1
    	return None
    ```
    
- 시간 복잡도는 $O(\log N)$ 보장

# 파이썬 이진 탐색 라이브러리

- 파이썬 bisect의 함수들
  - `bisect_left(a, x)`: 정렬된 순서를 유지하면서 배열 a에 x 를 삽입할 가장 왼쪽 인덱스를 반환
  - `bisect_right(a, x)`: 정렬된 순서를 유지하면서 배열 a에 x를 삽입할 가장 오른쪽 인덱스 반환
- 값이 특정 범위에 속하는 데이터의 개수 구하기
    
    ```python
    from bisect import bisect_left, bisect_right
    
    def count_by_range(a, left_value, right_value):
    	right_index = bisect_right(a, right_value)
    	left_index = bisect_left(a, left_value)
    	return right_index - left_index
    ```
    

# Parametric Search

- 최적화 문제를 결정 문제(예 / 아니오) 로 바꿔 해결하는 기법
- 이진 탐색을 이용하여 해결 가능
