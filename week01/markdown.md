# What is Markdown?

- 마크다운은 텍스트 기반의 가벼운 마크업 언어이다. 
- text 를 HTML 로 변환하는 도구
- 단순 텍스트 문법으로 내용을 작성하며, 다양한 환경(웹 페이지, 플랫폼 등)에서 변환하여 보여짐
- ex) README.md : 오픈소스의 공식 문서 작성 또는 개인 프로젝트의 프로젝트 소개서로 사용됨. 
- ex) 정적 사이트 생성기 기반 블로그(Jekyll, Gatsby, velog, ...) : 마크다운을 HTML, CSS, JS 파일 등으로 변환
- ex) Jupyter notebook의 Markdown cell, Notion 등

# Markdown 문법

## heading

- 문서의 제목이나 소제목으로 사용됨
- 문법 : `# 'title'` 
- #의 개수에 따라 대응되는 수준(heading level)이 있고, h1~h6 까지 표현 가능

## List

- 목록을 표현할 때 사용됨
- 순서가 없는 리스트(Unordered List, ul) 문법 : * 'content', - 'content'
- 순서가 있는 리스트(Ordered List, ol) 문법 : 1. 'content', 2. 'content' ... 

## Fenced Code Block

- 코드 블럭을 적용할때 사용됨
- 문법 : 'code' 를 ``` 으로 감싸줘 표현
- 첫 번째 ``` 뒤에 특정 언어를 적어 syntax highlighting을 표현 가능하다. 

## Inline Code Block

- 특정 단어에 코드 블럭을 적용할 수 있음
- 문법 :  ` 을 감싸줘 표현

## Link

- 문자열을 클릭하면 특정 url 에 연결되게 설정 가능
- 문법 : `[string](url)`로 표현 가능
- 디렉토리, 파일 등도 링크 가능하다. 

## Image

- 이미지를 삽입할 때 사용
- 문법 : `![string](url)`로 표현 

## Blockquotes 

- 인용문
- 문법 : `> string `

## Table

- extended syntax로, 지원하지 않는 플랫폼도 있다. 
- 문법
  - ```
    |text|text|
    
    |---|---|
    
    |test1|test2|
    ```


## 텍스트 강조

- Bold 문법 : `**string**, __string__`
- Italic 문법 : `*string*, _string_`

## 수평선

- 문법 : ***, ---, ___ 로 표현

## 취소선

- 문법 : `~~string~~`

## 마크다운 가이드 링크
- https://www.markdownguide.org/
