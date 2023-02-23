# CSS Box Model

- 모든 HTML요소를 사각형 박스로 표현
- 박스에 대한 크기, 여백, 테두리 등의 스타일을 지정하는 디자인 개념

## Box의 구성

- Margin
  - 해당 박스와 다른 요소 사이의 공백
  - 가장 바깥쪽 영역
  - Margin collapsing(마진 상쇄)
    - 두 **block 타입 요소**의 margin top과 bottom이 만나 큰 margin 으로 결합되는 현상
    - 웹 개발자가 레이아웃을 더욱 쉽게 관리할 수 있도록 함
- Border
  - 콘텐츠와 패딩을 감싸는 테두리 영역
- Padding
  - 콘텐츠 주위에 위치하는 공백 영역
- Content
  - 콘텐츠가 표시되는 영역
- `box-sizing` 속성을 통해 너비와 높이를 계산하는 기준을 설정할 수 있음
  - `border-box`, `content-box` 두 가지 값을 가질 수 있음

## Box Type

- Normal flow
  - CSS를 적용하지 않았을 때 Block 요소는 위에서 아래로, Inline 요소는 왼쪽에서 오른쪽으로 배치
- Block
  - 서로 margin으로 구분됨
  - 기본적으로 부모 요소 너비의 100%를 차지하며, 자식 컨텐츠의 최대 높이를 취함
  - 총 너비와 총 높이는 content + padding + border
- Inline
  - 새로운 행으로 나뉘지 않음
  - 자기 컨텐츠의 너비와 높이만 차지
  - width나 height 속성을 지정할 수 없음
  - `<img>` 는 inline 요소이지만, 다른 inline 요소들과 달리 width, heigth를 지정할 수 있음
  - Inline 요소의 크기를 제어하려면 block으로 변경하거나, inline-block요소로 설정해야 함
  - 수직 방향으로 padding, margin, borders 가 적용되지만 다른 요소를 밀어낼 수는 없음
  - 수평 방향으로 padding, margin, borders가 적용되고 다른 요소를 밀어낼 수 있음
- display 속성을 통해 inline, block 설정 가능
