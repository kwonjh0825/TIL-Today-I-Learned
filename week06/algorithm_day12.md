# 코딩테스트 모의고사 풀이

```python
# 1218: 괄호 짝짓기
for i in range(1, 11):
    n = int(input())
    string = input().strip()

    stack = []

    for s in string:
        if s in '({[<':
            stack.append(s)
        elif s == ')' and stack[-1] == '(':
            stack.pop()
        elif s == '}' and stack[-1] == '{':
            stack.pop()
        elif s == ']' and stack[-1] == '[':
            stack.pop()
        elif s == '>' and stack[-1] == '<':
            stack.pop()
        else:
            print(f'#{i} 0')
            break
    else:
        if stack:
            print(f'#{i} 0')
        else:
            print(f'#{i} 1')
```

- 처음에 다른 괄호 문제와 비슷하게 접근했는데 틀린 부분이 발생하여 다른 방식으로 바꾸었다.
- 여는 괄호가 나타나면 스택에 쌓고, 닫는 괄호가 나왔을 때 스택의 가장 마지막 원소가 닫는 괄호와 짝이 맞을 경우 pop을 하고 그렇지 않다면 0을 출력하도록 하였다.
- 모든 반복이 끝났을 때 스택이 비어있지 않다면 0, 비어있다면 1을 출력하도록 하였다.

```python
# 1225: 암호 생성기
from collections import deque

for _ in range(8):
    t = int(input())
    li = deque(list(map(int, input().split())))

    while li[-1] != 0:
        for i in range(1, 6):
            li.append(li.popleft() - i)
            if li[-1] < 1:
                li[-1] = 0
                break
    print(f'#{t}', end=' ')
    print(*li)
```

- 이 문제는 deque을 통한 큐를 이용해 해결하였다.
- 한 사이클 동안 i를 증가시키며 큐의 첫 번째 원소를 i만큼 빼고 다시 큐의 마지막에 추가하고, 만약 마지막 원소가 0이라면 모든 사이클을 종료하도록 작성하였다.

```python
# 1979: 어디에 들어갈 수 있을까
T = int(input())

for t in range(1, T+1):
    n, k = map(int, input().split())
    li = [list(map(int, input().split())) for _ in range(n)]

    rotated_li = list(zip(*li))

    row_cnt, col_cnt = 0, 0

    for l, rl in zip(li, rotated_li):
        len_r, len_c = 0, 0
        for i in range(n):
            if l[i]:
                len_r += 1
            else:
                if len_r == k:
                    row_cnt += 1
                    len_r = 0
                else:
                    len_r = 0
            if rl[i]:
                len_c += 1
            else:
                if len_c == k:
                    col_cnt += 1
                    len_c = 0
                else:
                    len_c = 0
        if len_r == k:
            row_cnt += 1
        if len_c == k:
            col_cnt += 1
    print(f'#{t} {row_cnt+col_cnt}')
```

- 처음에는 며칠 전 풀었던 문제와 같은 문제라고 생각하고 풀었지만, 문제의 조건이 달랐다.
- 빈 칸이 단어의 길이와 같은 공간만 카운트하는 조건이 있었다.
- 세로는 zip을 활용한 방식을 통해 행렬을 회전시켰다.

```python
# 1983: 조교의 성적 매기기
T = int(input())

grade = ['A+', 'A0', 'A-', 'B+', 'B0', 'B-', 'C+', 'C0', 'C-', 'D0']

for t in range(1, T+1):
    N, K = map(int, input().split())
    li = []
    for _ in range(N):
        mid, final, hw = map(int, input().split())
        li.append(mid*0.35 + final*0.45 + hw*0.2)
    score_sorted = sorted(li, reverse=True)
    rank = score_sorted.index(li[K-1])

    print(f'#{t} {grade[(rank//(N//10))]}')
```

- 이 문제는 학점을 인덱싱 하는 데 고생을 많이 했다.
- 점수를 계산식대로 입력하고 정렬한 리스트에서 k 번째 학생의 index를 찾아 순위로 설정하였다.
- 한 학점에 N//10 명 만큼 할당될 수 있으므로 순위를 N//10 으로 나누어 grade의 인덱스로 추가해 주었다.

```python
# 2001: 파리 퇴치
T = int(input())

for t in range(1, T+1):
    N, M = map(int, input().split())

    li = [list(map(int, input().split())) for _ in range(N)]
    kill_max = 0
    
    for i in range(N-M+1):
        for j in range(N-M+1):
            kill_now = 0
            for k in range(i, i+M):
                kill_now += sum(li[k][j:j+M])
            kill_max = max(kill_max, kill_now)
    
    
    print(f'#{t} {kill_max}')
```

- 이 문제는 완전탐색을 통해 해결하는 문제였다.
- 인덱스를 설정해 주는 것이 중요했는데, M칸만큼 계산하기 때문에 N-M+1 만큼 range에 설정하였다.
- 해당 칸부터 M개의 칸을 합한 수를 모아 한 번에 죽일 수 있는 파리의 수를 세었다.

```python
# 5431: 민석이의 과제 체크하기
T = int(input())

for t in range(1, T+1):
    N, K = map(int, input().split())
    li = list(range(1, N+1))

    stu = list(map(int, input().split()))
    for s in stu:
        li.remove(s)
    print(f'#{t}', end=' ')
    print(*li)
```

- 이 문제는 가장 쉽게 해결한 문제인 것 같다.
- N명만큼 리스트를 생성 후 과제를 제출한 사람을 리스트에서 제거해주는 방식을 통해 문제를 해결하였다.

# 모의고사 후기

- 이번 모의고사 문제들은 이때까지 풀었던 문제들보다 더 어려운 문제들이었던 것 같았다.
- 문제를 꼼꼼하게 읽지 않아 발생한 문제도 있었고, 처음 작성한 로직에 오류가 있었던 경우도 있었다.
- 문제를 꼼꼼히 읽고, 코드를 조금 더 좋게(더 많은 케이스를 고려한?) 작성해야 할 것 같다.