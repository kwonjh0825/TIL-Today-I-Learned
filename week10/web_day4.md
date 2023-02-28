# CSS Float

- 요소를 왼쪽이나 오른쪽으로 띄워서 텍스트 및 안라인 요소가 그 주위를 감싸도록 하는 배치
- 요소가 normal flow 에서 벗어남
- 탄생 배경
  - 신문 레이아웃 처럼 텍스트 열 내부에 떠다니는 이미지를 포함하면서도 해당 이미지의 좌우에 텍스트를 둘러싸는 간단한 레이아웃을 구현하기 위해 도입

# CSS Flexbox

- 요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식
- 요소 간 공간 배열과 정렬 가능

## 기본 사항

- Main axis(주 축)
  - flex item들이 배치되는 기본 축
  - main start에서 시작하여 main end 방향으로 배치
- Cross axis(교차 축)
  - main axis에 수직인 축
  - cross start에서 시작하여 cross end 방향으로 배치
- Flex container
  - `display: flex;` 혹은 `display: inline-flex;` 가 설정된 부모 요소
  - 이 컨테이너의 1차 자식 요소들이 flex item 이 됨
  - flexbox 속성 값들을 사용하여 자식 요소 flex item 들을 배치
- Flex item
  - Flex container 내부에 레이아웃 되는 항목

# Flexbox 레이아웃 구성

## Flexbox 속성

- Flex Container 관련 속성
  - display, flex-direction, flex-wrap, justify-content, align-items, align-content
- Flex item 관련 속성
  - oalign-self, flex-grow, flex-shrink, flex-basis, order

## Flex container 지정

- `display: flex;`를 통해 지정
- flex item 은 행으로 나열
- flex item 은 주축의 시작 선에서 시작
- flex item 은 교차축의 크기를 채우기 위해 늘어남

## 배치 설정

- Flex-direction
  - flex item 이 나열되는 방향을 지정
  - `row` (기본값): 주축은 가로, 교차축은 세로
  - `row-reverse`: 주축은 가로, 교차축은 세로, 주축의 시작과 끝이 반전
  - `column`: 주축은 세로, 교차축은 가로(주 축이 변경됨)
  - `column-reverse`: 주축은 세로, 교차축은 가로, 주축의 시작과 끝이 반전
- Flex-wrap
  - flex item 목록이 flex container 의 하나의 행에 들어가지 않을 경우 다른 행에 배치할지 여부를 결정하는 요소
  - `nowrap`(기본값): 요소를 줄이고 다른 행으로 배치하지 않음
  - `wrap`: 요소가 하나의 행에 들어가지 않을 경우 다른 행에 배치

## 공간 분배

- justify-content
  - flex item들을 주축에 따라 정렬하는 방법 지정
  - `flex-start` (기본값): 주축의 시작 선에 따라 정렬
  - `flex-end`: 주축의 끝 선에 따라 정렬
  - `center`: 주축의 중심선에 따라 정렬
  - `space-between`: flex item들 사이에 동일한 공간을 두고 정렬
  - `space-around`: flex item들 주위에 동일한 공간을 두고 정렬
- align-content
  - 교차축을 기준으로 flex item들 간의 간격을 지정하는 속성
    - flex-wrap 이 `wrap`, `wrap-reverse`로 설정된 여러 행에만 적용됨
    - 한줄 짜리 행에는 (`nowrap`) 효과 없음
  - `stretch` (기본값): flex item들을 교차축 방향으로 늘려서 채우기
  - `flex-start`: 교차축의 시작 선에 따라 정렬
  - `flex-end`: 교차축의 끝 선에 따라 정렬
  - `center`: 교차축의 중심선에 따라 정렬
  - `space-between`: flex item들 사이에 동일한 공간을 두고 정렬
  - `space-around`: flex item들 주위에 동일한 공간을 두고 정렬

## 정렬

- align-items
  - 교차축을 따라 flex item 정렬
  - `stretch` (기본값): flex item을 교차축 방향으로 늘려서 채우기
  - `flex-start`: 교차축의 시작 선에 따라 정렬
  - `flex-end`: 교차축의 끝 선에 따라 정렬
  - `center`: 교차축의 중심선에 따라 정렬
  - `baseline`: flex item의 baseline을 교차축의 같은 선에 맞추기
- align-self
  - 개별 flex item을 교차축을 따라 정렬하는 속성
  - `align-items` 속성과 동일한 값을 가지지만 flex item별로 개별 지정 가능
  - 기본값은 `stretch`

## flex-grow

- 남는 행 여백을 비율에 따라 각 flex item 에 분배

## flex-shrink

- 넘치는 너비를 분배해서 줄임

## flex-basis

- flex item의 초기 크기 값을 지정
- flex basis와 width 를 동시에 적용한 경우, flex-item 이 먼저 적용