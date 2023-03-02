# Semantic Web

- 웹 데이터를 의미론적으로 표현하고 연결하는 개념
- 컴퓨터가 데이터의 내용과 문맥을 더 효율적으로 이해하고 더 지능적으로 활용하기 위함

## HTML Semantic Element

- 기본적인 모양과 기능 이외에 의미를 가지는 HTML 요소
- 검색엔진 및 개발자가 웹 페이지의 콘텐츠를 이해하기 쉽게 만들어줌
- 대표적인 semantic element
  - header, nav, main, article, section, aside, footer

### heading

- 페이지 최상위 제목 의미를 제공하는 semantic 요소 h1
- 모든 요소를 최상위 제목처럼 보이게 할 수는 있지만 의미론적 가치는 없음

## OOCSS

- Object-Oriented CSS
- 객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론

## BEM 구성

- Block
  - 문단 전체에 적용된 요소 또는 요소를 담고 있는 컨테이너
  - 재사용 가능한 독립적 블럭, 가장 바깥쪽 상위 요소
  - 재사용을 위해 margin, padding  을 적용하지 않음
- Element
  - 주로 `block__element`로 작성
  - block이 포함하고 있는 한 조각
  - 블럭을 구성하는 종속적인 하위 요소
- Modifier
  - block 또는 element의 속성(color, size, …)
  - 주로 `block--modifier`로 작성