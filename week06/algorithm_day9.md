# 이차원 리스트 순회

- 이중 for문을 이용한 행 우선 순회
- 이중 for문을 이용한 열 우선 순회

# 전치

- 행렬의 행과 열을 서로 맞바꾸는 것을 의미
- 기존 행렬을 열 우선 순회 한 것과 유사

# 회전

- 이차원 리스트를 왼쪽, 오른쪽으로 90도 회전 하는 경우가 존재
- 오른쪽 90도 회전
  - 행은 기존의 열로 구성
  - 열은 (기존 길이) - (행) - 1 로 구성
- 왼쪽 90도 회전
  - 열은 기존의 행으로 구성
  - 행은 (기존 길이) - (행) - 1 로 구성

# 알고리즘 과제

```python
# pr01. 2441: 별 찍기-4
n = int(input())
for i in range(n):
    print(' '*i + '*'*(n-i))
```

- 이 문제는 앞에 공백과 별을 활용해 오른쪽 정렬을 구현하였다.
- f-string의 오른쪽 정렬을 구현한 방식이 인상적이었다.

```python
# pr02. 2592: 대표값
from collections import Counter 

li = [int(input()) for _ in range(10)]
cnt = Counter(li)
sorted_cnt = sorted(cnt.items(), key=lambda x: -x[1])

print(sum(li)//10, sorted_cnt[0][0])
```

- 이 문제는 평균과 최빈값을 찾는 문제로, 평균은 단순히 계산하였다.
- Counter 를 활용하여 해당 숫자가 나타난 빈도를 기록(?) 하여 내림차순으로 정렬한 후 첫 번째 원소를 출력하도록 하였다.

```python
# pr03. 10798: 세로 읽기
li = []
for i in range(5):
    li.append(list(input().strip()))
    if len(li[i]) < 15:
        li[i].extend([0] * (15 - len(li[i])))

for i in range(15):
    for j in range(5):
        if li[j][i] == 0:
            continue
        else:
            print(li[j][i], end='')
```

- 이 문제 같은 경우 list가 N x N 리스트로 주어지지 않기 때문에, 빈 칸은 0으로 초기화를 해 주었다.
- 리스트의 칸이 0일 경우, 즉 빈 칸일 경우 건너뛰고 아니라면 해당 리스트의 값을 출력하도록 하였다.

```python
# pr04. 9455: 박스
T = int(input())

for _ in range(T):
    box = []
    ans = 0
    m, n = map(int, input().split())
    for _ in range(m):
        box.append(list(map(int, input().split())))
    
    for i in range(n):
        cnt = 0
        for j in range(m-1, -1, -1):
            if box[j][i]:
                ans += cnt
            else:
                cnt += 1
    
    print(ans)
```

- 이 문제는 처음에 직접 박스를 옮기는 작업을 통해 해결하려고 했지만, 그 방식의 풀이는 실패하였다.
- 그래서 박스 별 움직여야 할 거리를 모두 세어서 더하는 방식을 통해 문제를 해결하였다.

```python
# pr05. 1652: 누울 자리를 찾아라
N = int(input())
room = [list(input().strip()) for _ in range(N)]
rotated_room = [['']*N for _ in range(N)]
for i in range(N):
    for j in range(N):
        rotated_room[i][j] = room[j][N-i-1]
ver_cnt = 0
hor_cnt = 0

for r, rr in zip(room, rotated_room):
    len_r = 0
    len_rr = 0
    for i in range(N):
        if r[i] == '.':
            len_r += 1
        elif r[i] == 'X':
            if len_r > 1:
                hor_cnt += 1
                len_r = 0
            else:
                len_r = 0
        
        if rr[i] == '.':
            len_rr += 1
        elif rr[i] == 'X':
            if len_rr > 1:
                ver_cnt += 1
                len_rr = 0
            else:
                len_rr = 0
    
    if len_r > 1:
        hor_cnt += 1                
    if len_rr > 1:
        ver_cnt += 1

print(hor_cnt, ver_cnt)
```

- 이 문제가 가장 어려웠는데, 사실 문제를 이해하는 데 시간이 오래 걸렸다.
- 빈칸 2칸이 있다면 누울 수 있고, 짐을 만나면 그 길이와 자리를 초기화하도록 코드를 작성했다.
- 세로로 계산하는 것은 행렬을 회전시켜 문제를 해결하였다.