# CSS Position

- normal flow에서 요소를 끄집어내서 다른 위치로 배치하는 것
- 다른 요소 위에 놓기, 화면 특정 위치에 고정시키기, …

## Position 유형

- static
  - 기본 값
  - normal flow에 따라 배치
- relative
  - 자기 자신을 기준으로 이동
  - normal flow에 따라 배치
  - 요소가 차지하는 공간은 static 일 때와 같음
- absolute
  - 요소를 normal flow에서 제거
  - 가장 가까운 relative 부모 요소를 기준으로 이동
  - 문서에서 요소가 차지하는 공간이 없어짐
- fixed
  - 요소를 normal flow에서 제거
  - 현재 화면영역(viewport)를 기준으로 이동
  - 문서에서 요소가 차지하는 공간이 없어짐
- sticky
  - 요소를 normal flow에 따라 배치
  - 가장 가까운 block 부모 요소를 기준으로 이동
  - 요소가 특정 임계점에 스크롤될 때 그 위치에서 고정됨(fixed)
  - 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky 요소의 자리를 대체

## z-index

- 요소가 겹쳤을 때 어떤 요소 순으로 위에 나타낼 지 결정
- z축(스크린 표면으로부터 사용자 얼굴 쪽으로 향하는 라인) 기준 정렬
- 더 큰 값을 가진 요소가 작은 값의 요소를 덮음