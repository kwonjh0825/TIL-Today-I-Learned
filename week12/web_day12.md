# Event

- 무언가 일어났다는 신호, 사건
- 모든 DOM 요소는 이러한 신호를 만들어 냄
- 종류: 마우스, 인풋, 키보드, 터치
- DOM요소는 event를 받고 받은 event를 처리할 수 있음

## event handler

- 이벤트가 발생했을 때 실행하는 함수
- 사용자의 행동에 어떻게 반응할지를 JS 코드로 표현한 것
- `.addEventListner()`
    - 대표적인 이벤트 핸들러 중 하나
    - 특정 이벤트를 DOM 요소가 수신할 때마다 콜백 함수 호출
    - 형식: `EventTarget.addEventListner(type, handler)`
        - EventTarget: DOM 요소
        - type: 특정 이벤트
        - handler: 콜백 함수