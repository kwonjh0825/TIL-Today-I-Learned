# 투 포인터

- 리스트에 순차적으로 접근해야 할 때 두 개의 점 위치를 기록하면서 처리하는 알고리즘
- 리스트에 담긴 데이터에 순차적으로 접근해야 할 때는 시작점과 끝점 2개의 점으로 접근할 데이터의 범위를 표현 가능
- ex) 특정한 합을 가지는 부분 연속 수열 찾기
  - 투 포인터 활용
    1. start, end가 첫 번째 원소의 인덱스를 가리키도록 함
    2. 현재 부분 합이 찾고자 하는 값과 같다면 카운트한다. 
    3. 현재 부분 합이 찾고자 하는 값보다 작다면 end를 1 증가시킨다. 
    4. 현재 부분 합이 찾고자 하는 값보다 크거나 같다면 start를 1 증가시킨다. 
    5. 모든 경우를 확인할 때까지 2번부터 4번까지의 과정 반복
  - python 구현 코드
        
        ```python
        count = 0
        interval_sum = 0
        end = 0
        for start in range(n):
        	while interval_sum < m and end < n:
        		interval_sum += data[end]
        		end += 1
        	if interval_sum == m:
        		count += 1
        	interval_sum -= data[start]
        ```
        

# 구간 합

- 연속적으로 나열된 N개의 수가 있을 때 특정 구간의 모든 수를 합한 값을 계산하는 문제
- 접두사 합: 배열의 맨 앞부터 특정 위치까지의 합을 미리 구해놓은 것
- 접두사 합 활용 알고리즘 과정
  1. N개의 수 위치 각각에 대하여 접두사 합을 계산하여 P에 저장
  2. 매 M개의 쿼리 정보를 확인할 때 구간 합은 P[right] - P[left-1] 
- 접두사 합을 활용한 python 구현 코드
    
    ```python
    sum_value = 0
    prefix_sum = [0]
    for i in data
    	sum_value += i
    	prefix_sum.append(sum_value)
    ```