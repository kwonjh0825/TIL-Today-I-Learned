## Improve Query

- 같은 결과에 대한 쿼리 개수를 줄여 조회하기

### annotate

- SQL의 GROUP BY 절 활용

### select_related

- 1:1 또는 N:1 참조 관계에서 사용
- SQL의 INNER JOIN 절 활용

### prefetch_related

- M:N 또는 N:1 역참조 관계에서 사용
- SQL이 아닌 python 을 사용한 join이 진행

## 비동기(Asynchronous)

- 작업을 시작한 후 결과를 기다리지 않고 다음 작업을 처리(병렬적 수행)
- 시간이 필요한 작업들은 요청을 보낸 뒤 응답이 빨리 오는 작업부터 처리

### Ajax(Asynchronous JavaScript And XML)

- 비동기적 웹 애플리캐이션 개발을 위한 프로그래밍 기술명
- 사용자의 요청에 대한 즉각적 반응을 제공하면서 페이지 전체를 다시 로드하지 않고 필요한 부분만 업데이트 하는 것 목표

### XMLHttpRequest

- JavaScript 객체로, 클라이언트와 서버 간 데이터를 비동기적으로 주고 받을 수 있도록 해주는 객체
- JavaScript 코드에서 서버에 요청을 보내고 서버로부터 응답을 받을 수 있음

## 비동기 요청

### Axios

- JavaScript에서 HTTP 요청을 보내는 라이브러리
- 주로 프론트엔드 프레임워크에서 사용
- cdn을 통해 불러와 사용

```html
axios({
	method: 'http method',
	url: 'request url',
})
	.then(성공 시 수행 콜백 함수)
	.catch(실패 시 수행 콜백 함수)
```