# Brute-force(무식하게 다 해보기)

- 무식하게 밀어붙인다는 뜻
- 가장 단순한 풀이 기법
- 단순 조건문과 반복문을 이용해서 풀 수 있음
- 복잡한 알고리즘보다 아이디어를 어떻게 코드로 구현할 것인지 중요

# Delta Search

- 이차원 리스트에서 탐색할 때 활용
- 이차원 리스트의 모든 원소를 순회하며(완전 탐색) 각 지점에서 상하좌우에 위치한 다른 지점을 조회하거나 이동하는 방식
- 이차원 리스트의 인덱스의 조작을 통해 상하좌우 탐색
- 행과 열의 변량인 -1, +1 을 delta값이라고 함
- 상하좌우 이동 후 범위를 벗어나지 않는지 확인 및 갱신

# 알고리즘 과제

```python
# pr01. 2525: 오븐 시계
a, b = map(int, input().split())
c = int(input())

b += c
if b >= 60:
    a += (b // 60)
    if a >= 24:
        a -= 24
    b = b % 60
print(a, b)
```

- 이 문제는 시간을 단순히 더하고, 시간이 24시가 지나면 24를 빼고, 분이 60을 넘는다면 60분당 1시간을 추가하고 60으로 나눈 나머지를 분으로 설정하여 해결하였다.

```python
# pr02. 2798: 블랙잭
from itertools import combinations

n, m = map(int, input().split())
li = list(map(int, input().split()))

combs = list(combinations(li, 3))
ans = 0
for c in combs:
    if sum(c) > m:
        continue
    elif sum(c) > ans:
        ans = sum(c)
print(ans)
```

- 이 문제는 combination을 통해 문제를 해결하였다.

```python
# pr03. 9076: 점수 집계
T = int(input())
for _ in range(T):
    li = sorted(list(map(int, input().split())))
    if li[-2] - li[1] > 3:
        print('KIN')
    else:
        print(sum(li[1:4]))
```

- 이 문제는 처음에는 모든 합을 구하는 것으로 착각하여 리스트에서 최대, 최소값을 지우지 않았는데 지우는 것이 더 좋을 것 같다.
- 입력받은 점수를 정렬하고 최대, 최소값을 제외한 점수 중 점수차가 4점 이상 난다면 KIN 을 출력하고, 아니면 최대, 최소값을 제외한 점수의 합을 출력하도록 하였다.

```python
# pr04. 1526: 가장 큰 금민수
for i in range(int(input()), 1, -1):
    for s in str(i):
        if s in '01235689':
            break
    else:
        print(i)
        break
```

- 이 문제는 가장 큰 수를 찾는 문제이기 때문에 입력받은 수부터 내림차순으로 정렬하여 완전탐색(?) 을 수행하였다.
- for-else 문을 통해 수에 4와 7을 제외한 숫자가 있다면 다음 수로 넘어가는 방식으로 문제를 해결하였다.

```python
# pr05. 1436: 영화감독 숌
n = int(input())
li = []
i = 1
while len(li) < 10001:
    if '666' in str(i):
        li.append(i)
    i += 1
print(li[n-1])
```

- 이 문제 역시 완전탐색을 활용하여 해결하였다. 666을 포함한 수를 list에 추가하고, n 번째로 큰 수를 출력하도록 하였다.