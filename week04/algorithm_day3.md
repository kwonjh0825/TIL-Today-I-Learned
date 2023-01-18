# 문자열 조작

- 문자열 슬라이싱
  - `s[2:5]`: index 2부터 4(5-1) 까지
  - `s[2:5:2]`: index 2 부터 4 까지 2칸마다
- 문자열 메서드
  - `s.startswith(a)`: 문자열이 a 로 시작하면 True, 아니라면 False 반환
  - `s.endswith(a)`: 문자열이 a 로 끝나면 True, 아니라면 False 반환
  - `s.find(a)`: 문자열에서 특정 문자 a가 처음 나타나는 index 반환, 없다면 -1 반환

# 아스키 코드

- 내장 함수
  - `ord(s)`: 문자 s를 아스키코드로 변환시켜 정수로 반환
  - `chr(i)`: 아스키 코드 i를 문자로 변환시켜 반환

# 3일차 과제

```python
# pr01. 9498: 시험 성적
n = int(input())

if n >=90:
    print("A")
elif n>=80:
    print("B")
elif n >= 70:
    print("C")
elif n >= 60:
    print("D")
else:
    print("F")
```

- 입력이  $0\le n \le 100$ 으로 주어지기 때문에, 위와 같은 코드를 작성해 봤다.

```python
# pr02. 9093: 단어 뒤집기
T = int(sys.stdin.readline())
for _ in range(T):
    li = list(sys.stdin.readline().split())
    for l in li:
        print(l[::-1], end=' ')
    print()
```

- 문자열을 공백을 기준으로 잘라 리스트로 저장하고 요소마다 거꾸로 출력하도록 하였다.

```python
# pr03. 11721: 열 개씩 끊어 출력하기
string = input()
for i in range(0, len(string), 10):
    print(string[i:i+10])
```

- for 문을 통해 0부터 10씩 증가시키면서 문자열에 접근하여 출력하도록 코드를 작성해보았다.

```python
# pr04. 2947: 나무 조각
li = list(map(int, input().split()))
while li != sorted(li):
    for i in range(4):
        if li[i] > li[i+1]:
            li[i], li[i+1] = li[i+1], li[i]
            print(*li)
```

- 입력받은 숫자를 리스트로 입력받고, 문제에 주어진 조건을 반복문으로 작성하였다.