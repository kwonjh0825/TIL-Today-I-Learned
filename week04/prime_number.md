# 소수(Prime Number)

- 1보다 큰 자연수 중, 1과 자기 자신을 제외한 자연수로 나누어떨어지지 않는 자연수
- 제일 기본적인 소수 판별 알고리즘
    
    ```python
    def is_prime(n):
    	for i in range(2, n):
    		if n & i == 0:
    			return False
    	return True
    ```
    
  - 위 알고리즘의 시간복잡도는 $O(n)$, n에 선형적으로 비례해 증가
- 약수의 성질
  - 모든 약수는 가운데 약수를 기준으로 곱셈에 대하여 대칭을 이룸
  - 모든 약수를 찾을 때, 가운데 약수(제곱근)까지만 확인하면 시간복잡도를 줄일 수 있음
- 약수의 성질을 활용한 소수 판별 알고리즘
    
    ```python
    def is_prime(n):
    	for i in range(2, int(n**1/2)+1):
    		if x % i == 0:
    			return False
    	return True
    ```
    
  - 위 알고리즘의 시간복잡도는 $O(\sqrt{n})$

# 에라토스테네스 체 알고리즘

- 다수의 자연수에 대해 소수 여부를 판별할 때 사용하는 대표적인 알고리즘
- n보다 작거나 같은 모든 소수를 찾을 때 사용할 수 있음
- 동작 과정
    1. 2부터 n까지의 모든 자연수 나열
    2. 남은 수 중 아직 처리하지 않은 가장 작은 수 i를 찾음
    3. 남은 수 중 i의 배수를 모두 제거
    4. 더 이상 반복할 수 없을 때까지 2~3 반복
- Python 구현 코드
    
    ```python
    def is_prime(n):
    	array = [False, False] + [True] * (n-1)
    	for i in range(2, int(n**1/2) + 1):
    		if array[i] == True:
    			for j in range(i*2, n+1, i):
    				ans[j] = False
    	if ans[n]:
    		return True         # n은 소수
    	else:
    		return False        # n은 소수가 아님
    ```
    
  - 시간 복잡도는 $O(n\log \log n)$으로, 사실성 선형 시간에 가까울 정도로 빠름
- 다수의 소수를 찾아야 하는 문제에서 효과적으로 사용 가능
- 각 자연수에 대한 소수 여부를 저장하므로 메모리가 많이 필요
