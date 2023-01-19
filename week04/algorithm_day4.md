# 해시 테이블

- 키를 값에 매핑할 수 있는 구조
- 해시 함수: 임의 길이의 데이터를 고정 길이의 데이터로 매핑하는 함수
- 해시: 해시 함수를 통해 얻어진 값

# Dictionary

- 파이썬의 dictionary 특징
  - 해시 함수와 해시 테이블을 이용
  - 삽입, 삭제, 수정, 조회 등의 연산 속도가 리스트보다 빠르다.  $O(1)$의 시간 복잡도
- 유용하게 사용할 때
  - key, value 구조로 관리를 해야 하는 경우 유용(순서나 인덱스가 아닌 경우)
  - 데이터에 대한 빠른 접근 탐색이 필요한 경우
- 기본 문법
  - `a_dict = {key1: value1, k2: value2, ...}`: 선언
  - `a_dict[key] = value`: 삽입 / 수정
  - `a_dict.pop(key, default)`: 삭제
  - `a_dict[key]`: 조회
  - `a_dict.get(key, default)`: 조회
  - `a_dict.keys()`: key 목록이 담긴 dict_keys 반환
  - `a_dict.values()`: value 목록이 담긴 dict_values 반환
  - `a_dict.items()`: (key, value) 쌍 목록이 담긴 dict_items 반환

# 4일차 과제

```python
# pr01. 2576: 홀수
num_li = [int(input()) for _ in range(7)]
odd_num = []
for num in num_li:
    if num % 2:
        odd_num.append(num)
if odd_num:
    print(sum(odd_num))
    print(min(odd_num))
else:
    print(-1)
```

- 이 문제 같은 경우 별도의 리스트에 홀수만 저장하여 해결하였다.

```python
# pr02. 10822: 더하기
print(sum(list(map(int, input().split(',')))))
```

- 이 문제는 입력으로 `,` 로 구분된 숫자들의 합을 구하는 것이었다. split 을 통하여 `,` 를 기준으로 숫자를 리스트에 담아 합을 구하였다.

```python
# pr03. 2754: 학점 계산
score_dict = {'A+': 4.3, 'A0': 4.0, 'A-': 3.7, 'B+': 3.3, 'B0': 3.0, 'B-': 2.7, 'C+': 2.3, 'C0': 2.0, 'C-': 1.7, 'D+': 1.3, 'D0': 1.0, 'D-': 0.7}
print(score_dict.get(input(), 0.0))
```

- 이 문제는 학점에 따른 점수를 dictionary에 저장한 후, 학점을 key로 받아 value를 출력하였다. F 학점은 dictionary에 저장하지 않았기 때문에 get 함수에서 default를 0.0 으로 설정해주었다.

```python
# pr04. 5622: 다이얼
dial = {'ABC': 3, 'DEF': 4, 'GHI': 5 , 'JKL': 6, 'MNO': 7, 'PQRS': 8, 'TUV': 9, 'WXYZ': 10}
string = input()
time = 0
for s in string:
    for j in dial:
        if s in j:
            time += dial.get(j)
            break
print(time)
```

- 이 문제는 걸리는 시간이 같은 문자를 모아 key로 설정하고 그에 따른 시간을 value로 지정한 dictionary 하나를 만든 후, 입력받은 문자열에 대하여 각 문자별 시간을 더하여 결과로 출력했다.
- 다른 조원의 경우 각 알파벳을 key로 하여 설정하였는데, 마지막 시간 계산 코드가 간략했던 것 같아 인상적이었다.

```python
# pr05. 2577: 숫자의 개수
import collections

num = [int(input()) for _ in range(3)]
result = 1
for n in num:
    result *= n
cnt = collections.Counter(str(result))
for i in range(10):
    print(cnt.get(str(i), 0))
```

- 이 문제 같은 경우 곱셈 결과를 문자열로 변환한 뒤, Counter를 사용하여 출력하였다. 특정 숫자가 나타나지 않는 경우 Counter에 나타나지 않기 때문에, get에서 default를 0으로 해주었다.

```python
# pr06. 7785: 회사에 있는 사람
import sys

n = int(sys.stdin.readline())

work = dict()
for _ in range(n):
    name, status = sys.stdin.readline().split()
    if status == 'enter':
        work[name] = 1
    else:
        work[name] = 0
print(*(sorted([w for w, s in work.items() if s == 1], reverse=True)), sep='\n')

# for w in sorted(work.items(), reverse=True):
#     if w[1] == 1:
#         print(w[0])
```

- 이 문제는 개인적으로 이때까지의 문제들 중 난이도가 조금 있다고 느껴졌다.
- 이 문제는 dictionary 구조에 이름을 key로 하고, value는 현재 회사에 있다면 1, 없다면 0으로 설정하도록 하였다. 출력할 때 현재 회사에 있는 사람들을 내림차순으로 정렬하여 출력하였다.
