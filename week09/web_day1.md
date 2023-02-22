# Web Page

- World Wide Web
  - 인터넷으로 연결된 컴퓨터들이 정보를 공유하는 거대한 정보 공간
- Web site
  - 인터넷에서 여러 개의 Web page가 모인 것으로 사용자들에게 정보나 서비스를 제공하는 공간
- Web page
  - HTML, CSS, JavaScript 등의 웹 기술을 이용하여 만들어진 하나의 인터넷 문서
- Web page가 모여서 Web site가 구성된다.
- Web 은 Web site, Web page를 포함하는 상위 개념

# Structuring web

## HTML

- HyperText Markup Language
- 웹 페이지의 의미와 구조를 정의하는 언어
- Hypertext
  - 웹 페이지를 다른 페이지로 연결하는 링크
  - 참조를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
- Markup Language
  - 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어
  - HTML, Markdown…

## HTML 구조

- Element
  - 하나의 요소는 여는 태그와 닫는 태그, 그 안의 내용으로 구성됨
  - 닫는 태그는 태그 이름 앞에 슬래시(/)가 포함됨
  - 태그가 없는 태그도 존재
- Attribute
  - 작성 규칙
    - 요소 이름 다음에 바로 오는 속성은 요소 이름과 속성 사이에 공백이 있어야 함
    - 하나 이상의 속성들이 있는 경우에는 속성 사이를 공백으로 구분
    - 속성 값은 열고 닫는 따옴표로 감싸야 함
  - 목적
    - 나타내고 싶지 않지만, 추가적인 기능과 내용을 담고 싶을 대 사용
    - CSS가 해당 요소를 선택하기 위한 값으로 사용됨
- Tag
  - `<title>`
    - 브라우저 탭 및 즐겨찾기 시 표시되는 제목으로 사용
  - `<head>`
    - 문서에 관련된 설명, 설정 등
    - 사용자에게 보이지 않음
  - `<body>`
    - 페이지에 표시되는 모든 컨텐츠
  - `<p>`
    - 한 문단임을 나타내는 태그
  - `<img>`
    - 이미지를 삽입할 수 있는 태그
  - `<ol>`
    - ordered list
    - 앞에 번호가 붙는 리스트
  - `<ul>`
    - unordered list
    - 순서가 없어 번호가 붙지 않는 리스트

## CSS

- Cascading Style Sheet
- 웹 페이지의 디자인과 레이아웃을 구성하는 언어
- CSS 구문
  - 선택자(Selector)
  - 선언(Declaration)
  - 속성(Property)
  - 값(Value)
- CSS 적용 방법
  1. 인라인 스타일
    - 태그 내 속성 값으로 추가하는 방식
  2. 내부(Internal) 스타일 시트
    - head 태그 내에 `<style>` 태그 내에 작성
  3. 외부(External) 스타일 시트
    - HTML과 CSS 파일을 분리하여 따로 작성
    - HTML 헤더 파일 내에 `<link>` 태그를 통해 불러옴
- 상속
  - CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속함
  - 코드 재사용성을 높임
  - 상속되는 속성
    - text 관련 요소(font, color, text-align), opacity, visibility 등
  - 상속되지 않는 속성
    - Box model 관련 요소, position 관련 요소

## CSS selectors

- HTML 요소를 선택하여 스타일을 적용할 수 있도록 함
- CSS selector 종류
  - 기본 선택자
    - 전체(*) 선택자
    - 요소(tag) 선택자
      - 지정한 모든 태그를 선택
    - 클래스(class) 선택자
      - 주어진 클래스 속성가진 모든 요소를 선택
      - ex) `.index` 는 `class=”index”` 를 가진 모든 요소를 선택
    - 아이디(id) 선택자
      - 주어진 아이디 속성을 가진 요소 선택
      - 문서에는 주어진 아이디를 가진 요소가 하나만 있어야 함
      - ex) `#index` 는 `id="index"` 를 가진 요소를 선택
    - 속성(attr) 선택자
  - 결합자
    - 자손 결합자(” “)
      - 직계 자식 뿐 아니라 그 아래 모두 적용
    - 자식 결합자(>)
- CasCade(계단식)
  - 동일한 우선순위를 갖는 규칙이 적용될 때 CSS에서 마지막에 나오는 규칙이 사용됨
- Specificity(우선 순위)
  - 선택자 별로 정해진 우선순위 점수에 따라 점수가 높은 규칙이 사용됨
  - 우선 순위
    1. ~~Importance~~ → Cascade 구조 무시하고 모든 우선순위 점수 계산을 무효화하는 가장 높은 우선순위. 반드시 필요한 경우가 아니라면 절대 사용하지 않는 것 권장
    2. 인라인 > id > class > 요소 선택자
    3. 소스 코드 순서