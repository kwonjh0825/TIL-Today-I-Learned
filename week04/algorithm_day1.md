# 1/16 → 알고리즘 1일차

## 알고리즘

- 어떤 문제를 해결하기 위해 정해진 일련의 절차나 행동
- 문제란 input을 넣었을 대 원하는 output이 나오도록 하는 것

## 코딩테스트에서 평가하는 두 가지 사항

- 문제 의도를 정확히 파악하고, 적절한 해결 방법을 적용할 수 있는가
- 해결 방법을 프로그래밍을 통해 능숙하게 구현할 수 있는가

## 1일차 과제

```python
# pr01. 10039: 평균 점수
scores = []
for _ in range(5):
    score = int(input())
    scores.append(scores) if score > 40 else scores.append(40)
print(int(sum(scores)/len(scores)))
```

- 코드 리뷰 시간에 다른 조원들의 코드를 보았을 때, 리스트에 저장하지 않고 for문에서 sum 변수에 입력을 바로 더하는 경우가 있었다. 메모리를 절약할 수 있는 좋은 코드였던 것 같아 나중에 그렇게 작성할 수 있도록 해야할 것 같다.

```python
# pr02. 10871: x보다 작은 수
n, x = map(int, input().split())
li = list(map(int, input().split()))
for num in li:
    if num < x:
        print(num, end=' ')
```

- 이 코드 같은 경우, filter 내장 함수를 통해 푼 조원이 있었는데, 다음에 비슷한 문제나 상황이 주어진다면 filter 함수를 통해 풀어봐야겠다.

```python
# pr03. 2480: 주사위 세개
num_li = sorted(map(int, input().split()))
t = len(set(num_li))
if t == 1:
    print(10000+(num_li[0]*1000))
elif t == 2:
    print(1000+(num_li[1]*100))
else:
    print(100*(max(num_li)))
```

- 이 방식 같은 경우, 주사위가 3개 가 아니게 되면 코드를 고쳐야 하겠지만, 문제의 주사위는 3개 였기 때문에 이런 방식으로 코드를 작성 해보았다.

```python
# pr04. 10886: 0 = not cute / 1 = cute
N = int(input())
survey = [int(input()) for _ in range(N)]
ans = 0 if survey.count(1) > survey.count(0) else 1 # 0: cute, 1: not cute
print('Junhee is ' + (ans * 'not ') + 'cute!')
```

- 사실 이 코드를 작성하면서, 가독성이 떨어진다고 생각했다. 문제의 입력에서 0은 귀엽지 않고, 1은 귀여움을 의미하는데, ans 변수의 0은 귀여움을, 1은 귀엽지 않음을 의미하기 때문에 헷갈릴 수 있을 것 같았기 때문이다. 다음엔 그냥 if 문을 통해 작성할 것 같긴 하다.

```python
# pr05. 2506: 점수 계산
N = int(input())
score = list(map(int, input().split()))
ans, cnt = 0, 0
for s in score:
    if s:
        cnt += 1
        ans += cnt
    else:
        cnt = 0
print(ans)
```

- 다른 조원의 풀이 중 `input().split(0)`가 있었는데, 0을 기준으로 나눠 1의 갯수만큼 가우스 합을 적용시켜 코드를 작성했는데, 한번도 생각해보지 못한 방법이여서 참신하고 좋은 코드였던 것 같다.