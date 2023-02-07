# 단순 구현

- 기본 코딩테스트
  - 주로 문제의 내용을 코드로 구현 가능한지 테스트
  - 문제 풀이에 시간 제한이 없는 경우가 많기 때문에 시간 복잡도를 생각하지 않고 풀어보는 것이 좋다
  - 완전 탐색 중에서도 2차원 배열 탐색, 델타 탐색 등 선형 탐색이 주를 이룸
- 단순 구현
  - 문제에 제시된 풀이 과정을 그대로 구현하는 유형
  - 시뮬레이션의 경우, 완전 탐색 유형 중 하나로써 모든 경우의 수를 탐색하며 풀이
  - 문제에 제시도니 과정을 그대로 구현할 수 있는가가 핵심

# 알고리즘 과제

```python
# pr01. 17608: 막대기
import sys

input = sys.stdin.readline

N = int(input())
li = [int(input()) for _ in range(N)]
max_height = 0
cnt = 0
for l in reversed(li):
    if l > max_height:
        cnt += 1
        max_height = l
print(cnt)
```

- 오른쪽에서 막대기를 쳐다보기 때문에 오른쪽 막대기부터 역순으로 순회하였다.
- 순회한 막대기 중 최대 높이의 막대기보다 작은 막대기는 보이지 않기 때문에 카운트 하지 않고, 카운트된다면 최대 막대기 높이를 갱신하였다.

```python
# pr02. 7568: 덩치
n = int(input())
li = []
cnt_list = []
for i in range(n):
    li.append(list(map(int, input().split())))
for i in li:
    cnt = 1
    for j in li:
        if i[0] < j[0] and i[1] < j[1]:
            cnt += 1
    cnt_list.append(cnt)

print(*cnt_list)
```

- 이 문제에서는 키와 몸무게가 둘 다 커야 덩치가 더 크다.
- 자신보다 더 큰 덩치를 가진 사람을 만나면 카운트를 1 추가하는 방식으로 등수를 측정했다.

```python
# pr03. 1063: 킹
a, b, n = input().split()
n = int(n)

direction = {'R': (1, 0), 'L': (-1, 0), 'B': (0, 1), 'T': (0, -1), 'RT': (1, -1), 'LT': (-1, -1), 'RB': (1, 1), 'LB': (-1, 1)}
king_x, king_y = ord(a[0]) - 65, 8 - int(a[1])
stone_x, stone_y = ord(b[0]) - 65, 8 - int(b[1])

for _ in range(n):
    t = input()
    king_nx, king_ny = king_x + direction[t][0], king_y + direction[t][1]
    if 0 <= king_nx < 8 and 0 <= king_ny < 8:
        if (king_nx, king_ny) == (stone_x, stone_y):
            stone_nx, stone_ny = stone_x + direction[t][0], stone_y + direction[t][1]
            if 0 <= stone_nx < 8 and 0 <= stone_ny < 8:
                stone_x, stone_y = stone_nx, stone_ny
                king_x, king_y = king_nx, king_ny
        else:
            king_x, king_y = king_nx, king_ny
print(f'{chr(king_x+65)}{8 - king_y}', f'{chr(stone_x+65)}{8-stone_y}', sep='\n')
```

- 처음에는 킹과 돌의 위치를 계산하기 쉽게 평면좌표 상으로 옮겼다.
- 이후 방향에 따라 좌표를 계산 후 이동하는 조건에 맞게 킹과 돌을 이동시켰다.
- 이후 평면좌표 상 좌표를 다시 체스판 좌표에 맞게 출력하였다.