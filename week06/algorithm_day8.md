# 이차원 리스트

- 이차원 리스트는 리스트를 원소로 가지는 리스트
- 보기 좋게 변경하면 행렬의 형태를 가짐
- List Comprehension을 통해 만들 수 있음
- 입력 받기

# 알고리즘 과제

```python
# pr01. 1225: 이상한 곱셈
n, m = input().split()
n = list(map(int, n))
m = list(map(int, m))
print(sum(n)*sum(m))
```

- 이 문제는 처음에 for문으로 작성 했을 때 시간초과가 나왔다.
- 계산 식을 수학적으로 생각하고, 인수분해를 활용하여 코드를 작성하니 해결되었다.

```python
# pr02. 2438: 별 찍기-1
for i in range(1, int(input())+1):
    print('*'*i)
```

- 이 문제는 별표 개수를 문자열 곱셈 형식으로 출력하여 해결하였다.

```python
# pr03. 2739: 구구단
n = int(input())
for i in range(1, 10):
    print(f'{n} * {i} = {n*i}')
```

- 이 문제는 입력받은 수에 대해 반복적으로 구구단을 f-string 형식으로 출력하여 해결하였다.

```python
# pr04. 2953: 나는 요리사다
li = [list(map(int, input().split())) for _ in range(5)]
ans = 0
idx = 0
for i, l in enumerate(li):
    if sum(l) > ans:
        idx = i+1
        ans = sum(l)
print(idx, ans)
```

- 이 문제는 이중 리스트로 각 점수를 저장하고, enumerate 함수를 사용해 점수가 가장 높은 사람의 index를 저장하고 점수도 저장하여 해결하였다.

```python
# pr05. 2669: 직사각형 네개의 합집합의 넓이
ground = [[0] * 101 for _ in range(101)]
ans = 0
for _ in range(4):
    x1, y1, x2, y2 = map(int, input().split())
    for x in range(x1, x2):
        for y in range(y1, y2):
            ground[x][y] = 1
for g in ground:
    ans += g.count(1)
print(ans)
```

- 오늘은 이 문제가 가장 난이도가 있었던 것 같다.
- 처음에는 넓이를 계산하고 겹치는 부분을 계산하여 계산식으로 해결하려 했지만, 해결 방법을 찾지 못해 다른 방식으로 해결하였다.
- 좌표평면을 땅이라고 생각하고, 그 한칸에 사각형이 포함되어 있으면 1, 없으면 0으로 만들어 1의 개수를 세는 방식으로 해결하였다.