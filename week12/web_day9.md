# JavaScript의 역사

## JavaScript의 탄생

- Netscape는 Microsoft의 IE와 경쟁할 차기 웹 브라우저 개발 착수
- Netscape는 웹 페이지에 동적인 기능을 제공하기 위한 새로운 언어 개발 시작
- Netscape 소속 개발자 Brandon Eich 가 Mocha 라는 언어 개발
- 이후 LiveScript로 이름을 변경 했으나 당시 인기있던 자바의 명성에 기대보고자 JavaScript로 이름 변경

## JavaScript의 파편화

- Microsoft는 JavaScript의 파생버전인 Jscript를 IE 3.0에 채택
- 이 과정에서 Netscape와 Microsoft, 그리고 많은 회사들이 자체적으로 JavaScript를 탑재해 독자적으로 업데이트
- 이로 인해 같은 코드가 브라우저마다 다르게 동작하는 등의 문제가 발생, 추후 JavaScript 표준화의 배경

## 1차 브라우저 전쟁

- Microsoft가 IE를 자사 윈도우 운영체제에 내장하여 무료로 배포
- 빌 게이츠를 필두로 한 MS의 공격적 마케팅, 자금력, 막강한 윈도우 운영체제 점유율 앞에 Netscape는 빠르게 몰락하기 시작
- IE의 시장 점유율이 2002년 약 96%에 달하며 MS의 승리로 종료
- 추후 Brandon Eich 와 함께 Netscape에서 나온 핵심 개발진은 모질라 재단을 설립하여 2003년 Firefox 출시

## 2차 브라우저 전쟁

- 2008년 구글에서 Chrome 출시
- 출시 3년 만에 10년간 쌓아온 Firefox의 점유율을 넘어섰고 그로부터 반년 뒤 IE의 점유율을 넘어섬
- 빠른 속도, 압도적 성능, 엄격한 웹 표준 준수, 강력한 개발자 도구 제공
- 웹 표준의 발전과 웹 애플리케이션의 대중화에 큰 역할

## JavaScript 현황

- 현재는 Chrome, Firefox, Safari, Microsoft Edge 등 다양한 웹 브라우저가 출시되어 있으며 웹 브라우저 시장이 다양화 되어 있음
- 기존 JavaScript는 브라우저에서만 웹 페이지의 동적인 기능을 구현하는 데 사용
    - 사용자의 입력에 따라 웹 페이지의 내용이 동적으로 변경되거나 애니메이션 효과가 적용되는 등
- 이후 브라우저에서 벗어나 Node.js와 같은 서버 사이드 분야 뿐 아니라 다양한 프레임워크와 라이브러리들이 개발되면서 웹 개발 분야에서는 필수적인 언어로 자리잡게 됨

# JavaScript의 표준화

## ECMAScript

- Ecma International 이 정의하고 있는 표준화된 스크립트 프로그래밍 언어
- JavaScript의 파편화를 마기 위해 1997년 ECMA에서 ECMAScript라는 표준 언어 정의
- 이후 ECMAScript는 독자적으로 발전하며 JavaScript보다 더 많은 기능을 제공하게 됨
- 2009년에는 ECMAScript 5(ES5)에서 안정성과 생산성을 크게 높임
- 2015년에는 ECMAScript 2015(ES6)에서 객체지향 프로그래밍 언어로써 많은 발전을 이루어 역사상 가장 중요한 버전으로 평가됨
- JavaScript는 ECMAScript의 구현 언어 중 하나

# DOM

- Document Object Model
- 웹 페이지를 구조화된 객체로 제공하며 프로그래밍 언어가 웹 페이지를 사용할 수 있게 연결시킴
- 문서는 웹 브라우저를 통해 해석되어 화면에 나타남
- DOM은 이러한 문서를 조작하는 방법을 제공하는 API
- 브라우저는 HTML 문서를 해석하여 DOM tree 라는 객체의 트리로 구조화함
- DOM에서 모든 요소, 속성, 텍스트는 하나의 객체이며 모두 document 객체의 자식
- 웹 페이지를 동적으로 만드는 것→웹 페이지를 조작하는 것
- 조작하기 위한 순서
    1. 조작 하고자 하는 요소 선택 또는 탐색
    2. 선택된 요소의 컨텐츠 또는 속성 조작
- ‘document’ object
    - 웹 페이지 객체
    - DOM Tree의 진입점
    - 페이지를 구성하는 모든 객체 요소 포함

## DOM Query(선택)

- `document.querySelector()`: 요소 하나 선택
- `document.querySelectorAll()`: 요소 여러 개 선택

## DOM Manipulation

- 속성 조작
    - `classList` property
        - 요소의 클래스 목록을 DOMTokenList(유사 배열) 형태로 반환
        - add(), remove() 메서드를 사용해 지정한 클래스 값을 추가, 제거
- HTML 컨텐츠 조작
    - `textContent` property
        - 요소의 텍스트 컨텐츠를 표현
- DOM 조작
    - `createElement()`: 요소 선택
    - `.appendChile()`: 요소 추가
    - `.removeChild()`: 요소 삭제
- style 조작
    - 해당 요소의 모든 스타일 속성 목록을 포함하는 속성