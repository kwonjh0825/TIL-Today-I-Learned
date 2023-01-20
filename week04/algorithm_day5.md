# 코딩테스트 모의고사 풀이 코드

```python
# 1204. 최빈수 구하기
T = int(input())
for _ in range(T):
    t = int(input())
    score_dict = {}
    for score in list(map(int, input().split())):
        score_dict[score] = score_dict.get(score, 0) + 1
    result = sorted(score_dict.items(), key=lambda x: (x[1],x[0]), reverse=True)
    print(f'#{t} {result[0][0]}')
```

- 이 문제는 입력 점수가 1000개 이기 때문에 바로 dictionary 를 사용해야겠다고 생각하였다.
- 점수의 빈도를 dictionary 에 저장한 후 sorted 함수를 통해 정렬하였다.

```python
# 3456. 직사각형 길이 찾기
T = int(input())

for t in range(1, T+1):
    len_dict = {}
    for s in map(int, input().split()):
        len_dict[s] = len_dict.get(s, 0) + 1
    
    for s, cnt in len_dict.items():
        if cnt % 2:
            print(f'#{t} {s}')
            break
```

- 이 문제 같은 경우, 두 변의 길이가 같은 경우와 세 변의 길이가 같은 경우 두 가지 경우의 수가 있었다.
- 두 변의 길이가 같은 경우는 나머지 한 변의 길이를, 세 변의 길이가 같은 경우 똑같은 길이를 출력하면 되는 문제라고 생각했다.
- dictionary에 입력 빈도를 저장하고, 홀수 번 입력받은 변의 길이를 출력하도록 코드를 작성했다.

```python
# 10505. 소득 불균형
T = int(input())
for t in range(1, T+1):
    n = int(input())
    li = list(map(int, input().split()))
    avg = sum(li) / n
    ans = list(filter(lambda x: x <= avg, li))
    print(f'#{t} {len(ans)}')
```

- 이 문제 같은 경우 리스트에 입력을 다 받고, filter 함수를 통해 평균 이하의 입력들로 새로운 리스트를 만들어 그 리스트의 길이를 출력하도록 했다.

```python
# 10804. 문자열의 거울상
T = int(input())
mirror = {'b': 'd', 'd': 'b', 'p': 'q', 'q': 'p'}
for t in range(1, T+1):
    string = input()
    print(f'#{t} ', end='')
    for s in string[::-1]:
        print(f'{mirror.get(s)}', end='')
    print()
```

- 이 문제는 예시를 보고 문제를 이해했다. 거울에 비치기 때문에 입력받은 역순으로 알파벳을 뒤집어 출력하는 형태의 문제였다.
- 거울에 비쳐 나타나는 문자를 dictionary에 저장하고, 입력받은 문자를 역순으로 순회하며 key에 맞는 value를 출력하도록 하였다.

```python
# 14649. 신용카드 만들기 1
T = int(input())

for t in range(1, T+1):
    li = list(map(int, input().split()))
    result = 0
    for i in range(15):
        if i % 2:
            result += li[i]
        else:
            result += 2 * li[i]
    print(f'#{t} {(10 - (result % 10)) % 10}')
```

- 이 문제는 카드 16자리의 마지막 16번째 수를 맞추는 문제로, 규칙에 따라 합을 구하고 그에 따른 16번째 값을 출력하도록 하였다.
- 규칙의 합이 10으로 나누어 떨어진다면 10 - 0을 하는 경우 10이 나오기 때문에, 마지막 출력 구문처럼 그 결과를 10에서 뺀 것을 10으로 나눈 나머지를 출력하도록 하였다.

```python
# 14654. 신용카드 만들기 2
T = int(input())

for t in range(1, T+1):
    car_no = input()
    car_no = ''.join(list(car_no.split('-')))
    if car_no[0] in '34569' and len(car_no) == 16:
        print(f'#{t} 1')
    else:
        print(f'#{t} 0')
```

- 이 문제 같은 경우, 입력으로는 카드 번호가 주어지는데 -가 있는 카드번호도 있고 없는 카드번호도 주어진다.
- 입력 받은 후, -를 기준으로 split을 수행하고, 숫자 부분의 길이가 16이고 3, 4, 5, 6, 9로 시작하는지 확인하였다.

# 모의고사 후기

- 이번 모의고사 문제들은 문제 자체가 크게 어렵다고 느껴진 부분은 없었다.
- 하지만 SWEA의 출력 형식에 맞추지 않아 틀렸는데, 이걸 발견하는 데 시간이 많이 걸렸던 것 같다.
- 앞으로는 문제와 내가 작성한 코드를 좀 더 자세히 읽어봐야 할 것 같다는 생각이 든다.