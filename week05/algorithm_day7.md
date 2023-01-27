# 힙(Heap)

- 우선순위 큐: 우선순위를 기준으로 가장 우선순위가 높은 데이터가 가장 먼저 나가는 방식
- 우선순위 큐를 구현하는 방법
  - 배열
  - 연결 리스트
  - 힙
- 힙의 특징
  - 최대값 또는 최소값을 빠르게 찾아내도록 만들어진 데이터 구조
  - 완전 이진 트리의 형태로 느슨한 정렬 상태를 지속적으로 유지한다.
  - 힙 트리에서는 중복 값을 허용
  - 삽입, 삭제 시간 복잡도가 $O(\log N)$ (리스트의 경우 최악으로 $O(N)$ 걸림)
- 데이터가 지속적으로 정렬되거나 데이터에 삽입/삭제가 빈번한 경우 사용
- python 의 heapq 모듈
  - 최소 힙으로 구현되어 있음
  - 삽입, 삭제, 수정, 조회 연산의 속도가 리스트보다 빠르다

# 셋(Set)

- 수학에서 집합을 나타내는 데이터 구조
- Set의 연산
  - `.add()`
  - `.remove()`
  - 합집합( | )
  - 차집합( - )
  - 교집합( & )
  - 대칭 차집합( ^ )
- 데이터의 중복이 없어야 할 때, 정수가 아닌 데이터의 삽입/삭제/탐색이 빈번히 필요할 때 사용

# 알고리즘 과제

```python
li = list(map(int, input().split()))
print(sorted(li)[1])
```

- 이 문제는 세 수중 두번째로 큰 값, 즉 가운데 값을 출력하는 문제이다. 수의 개수가 많지 않기 때문에 리스트를 통해 문제를 해결하였다.

```python
input()
pro = 0
while True:
    string = input()
    if string == '문제':
        pro += 1
    elif string == '고무오리':
        if pro:
            pro -= 1
        else:
            pro += 2
    else:
        break
if pro:
    print('힝구')
else:
    print('고무오리야 사랑해')
```

- 이 문제는 첫 번째와 마지막을 제외하고 문제와 고무오리가 반복적으로 나온다. 남아있는 문제의 개수를 변수에 저장하는 형식으로 문제를 해결하였다.

```python
_, _ = map(int, sys.stdin.readline().split())

a = set(map(int, sys.stdin.readline().split()))
b = set(map(int, sys.stdin.readline().split()))

a_b = a - b
b_a = b - a
print(len(a_b)+len(b_a))
```

- 이 문제는 대칭 차집합 문제로, A-B 한 결과와 B-A 한 결과의 갯수를 더하여 해결하였다.

```python
i = set()

for _ in range(10):
    li.add(int(input())%42)
print(len(li))
```

- 이 문제는 입력받은 수에 대해 42로 나눈 나머지의 개수를 구하는 문제이다. 중복된 수가 필요없기 때문에 set을 활용하여 문제를 해결하였다.

```python
n = int(sys.stdin.readline())
li = []
for _ in range(n):
    li.append(sys.stdin.readline().strip())
li = set(li)
print(*sorted(li, key=lambda x: (len(x), x)), sep='\n')
```

- 이 문제는 입력받은 문자에 대해 길이순으로 정렬하고, 길이가 같다면 사전순으로 정렬하는 문제다. 같은 문자에 대해서는 한 번 출력하기 때문에 set을 활용하여 문제를 해결하였다.

```python
N = int(input())
heap = []
for _ in range(N):
    x = int(input())
    if x == 0: 
        if heap:
            print(heapq.heappop(heap)[1])
        else:
            print(0)
    else:
        heapq.heappush(heap, (abs(x), x))
```

- 이 문제는 절댓값 heap를 구현하는 문제로, 절대값을 기준으로 정렬하는 heap을 구현해야 한다. 그래서 heap의 원소로 절댓값과 원래 입력값 두 가지를 사용해 문제를 해결하였다.