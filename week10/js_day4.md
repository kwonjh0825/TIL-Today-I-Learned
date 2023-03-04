# 함수

- `function function_name(var) { 함수내용 }` 으로 선언
- 함수명은 읽기 쉽고 어떤 동작인지 알수 있도록 작성
- 지역변수: 함수 내부에서만 사용 가능한 변수, 함수 밖에서 접근 시 에러 발생
- 전역변수: 어디서나 접근 가능한 변수
- 전역변수가 많아진다면 변수 관리가 힘들 수 있기 때문에 적절하게 사용해야 함
- `return`: 이후 변수를 결과로 반환하고 함수를 종료

# 함수 표현식

## 함수 선언문

- `function func_name() { 함수 내용 }` 과 같은 형식
- 어디서든 호출이 가능함

## 함수 표현식

- `let funcname = function() { 함수내용 }` 과 같은 형식
- 생성 이후 구문에서만 호출 가능

## 화살표 함수

- 함수를 간단하게 표현하는 방법

```jsx
// 함수 내부가 여러 줄일 경우
let add = function(num1, num2) {
	const result = num1 + num2;
	return result;
}
// 일반적인 화살표 함수
let add = (num1, num2) => { 
	return num1 + num2;
}
```