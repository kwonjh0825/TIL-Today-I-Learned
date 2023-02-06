# openpyxl

- 파이썬에서 엑셀처리를 할 수 있는 파이썬 외부 라이브러리
- Excel 2010 이상의 xlsx, xlsm, xltx, xltm 파일 처리 가능
- 엑셀의 설치여부와 무관하게 처리할 수 있음
- 엑셀 작업 주요 프로세스
  1. 모듈 import
  2. 워크북을 열어 핸들러를 얻음
  3. 워크시트의 핸들러를 얻음
  4. 시트의 cell(행, 열)을 이용하여 작업
- 행과 열의 사이즈 지정
  - `sheet.row_dimensions[idx].height = (높이)`: 행의 높이 지정
  - `sheet.column_dimensions[col].width = (너비)`: 열의 너비 지정
- 정렬방식, 폰트지정, 선긋기: styles 객체의 Alignment, Font, Border, Side 클래스 활용
- 모든 열을 대상으로 작업: sheet 객체의 colums 활용
- 모든 행을 대상으로 작업: sheet 객체의 rows 활용
- 특정 셀 집합에 대한 슬라이싱 가능
    
    ```python
    m_cell = sh['c1':'e7']
    for row in m_cell:
    	for cell in row:
    		print(cell.value)
    ```
    
- 행, 열 추가 및 삭제: insert(delete)_rows(cols)
- 셀 병합: merge_cells
- 시트 추가: create_sheet