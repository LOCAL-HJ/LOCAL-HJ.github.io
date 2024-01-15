---
title: "[클라우딩 어플리케이션 엔지니어링] TIL DAY 2 (12/19)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 2일차"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til2

toc: true
toc_sticky: true

date: 2023-12-19
last_modified_at: 2023-12-19
---

## [Facts]

- HTML 공부

## [TIL]

### HTML

- HTML 기본 문법
  - 콘텐츠를 가지는 태그
    - 열리는 태그(시작 태그), 닫히는(종료 태그) 태그 존재
    - ex) `<div> 콘텐츠 </div>`
  - 콘텐츠를 가지지 않는 태그
    - 단일 태그 (Empty Element)
    - ex) `<br />`
- 속성과 값
  ```html
  <a href="#"> Google </a>
  <!-- href : 속성 (Attribute) , #: 값(value), Google: 콘텐츠(content)-->
  ```
- HTML 기본 문서

  ```html
  <! DOCTYPE html>
  <!--문서버전-->
  <html lang="ko">
    <!--HTML 문서 시작 선언 및 문서 기본언어 설정-->
    <head>
      <!--문서에 필요한 정보가 기입되는 곳-->
      <title>문서 제목</title>
      <!--문서의 제목-->
    </head>

    <body>
      프로그래머스 데브코스
      <!--실제 사용자가 눈으로 볼 수 있는 문서의 내용이 입력되는 곳-->
    </body>
  </html>
  ```

- 부모 요소 자식 요소
  - html 코드는 부모 자식 요소로 구성되어있음
  - 따라서 들여쓰기, 내어쓰기 잘해야함
- HTML 주석
  - 주석 (comment) : 개발자가 코드 내에 입력한 메모
  - 기본 사용법 : `<!-- 주석 내용 -->` >> 줄바꿈도 가능
  - 주석 안에 주석은 안된다
  - 사용자에게는 보이지 않는 주석이지만, 소스보기나 개발자 도구로 보면 코드가 보이니 조심!

### HEAD

- `<head>`
  - 사람 눈에 보이지 않는 문서의 정보가 담기는 영역
  - `<head>`가 가질 수 있는 정보의 종류
    1. 타이틀
    2. 메타데이터
       1. 인코딩 정보
          - charset(character set)은 문서에서 허용하는 문자의 집합
          - charset에 선언된 문자의 집합 규칙에 따라 문서에서 사용할 수 있는 문자가 제한된다
          - `<meta charset= “ ”>`
       2. 문서 설명
       3. 문서 작성자
    3. CSS, Script
- style, link, script
  - `<style>`, `<link>`, `<script>` : 문서 내용의 외형에 영향을 주는 태그들
  - style
  - link : `<link rel= “stylesheet” href= “style.css” />`
  - script
    - 콘텐츠 방식
      ```html
      <script>
        const hello = "world";
        console.log(hello);
      </script>
      ```
    - 링크 방식 : `<script src= “script.js”></script>`

### BODY

- `<body>` : 사람 눈에 실제로 보이는 콘텐츠 영역
- block, inline, inline-block
  - block (블록 레벨 요소)
    - 레고 블록처럼 차곡차곡 쌓이고 화면 너비가 꽉 차는 요소
      - 블록의 크기와 내/외부에 여백을 지정할 수 있고 일반적으로 페이지의 구조적 요소를 나타낸다
      - 인라인 요소를 포함할 수 있으나, 인라인 요소에 포함될 수 없다
    - 대표적인 블록 레벨 요소 : `<div>`, `<article>`,`<section>`
  - inline(인라인 레벨 요소)
    - 블록 요소 내에 포함되는 요소
      - 주로 문장, 단어 같은 작은 부분에 사용되며 한줄에 나열된다
      - 좌우에 여백을 넣는 것만 허용
    - 대표적인 인라인 레벨 요소: `<span>`, `<a>`, `<strong>`
  - inline-block
    - 글자처럼 취급되나, block 태그의 성질을 가지는 요소
    - block과 마찬가지로 크기와 내/외부 여백을 지정할 수 있다.
    - CSS로 성질을 바꾼것이기 때문에 의미상 인라인 레벨 요소이다.

### 레이아웃

<img width="395" alt="layout" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/fbd8e817-8b55-4104-a35e-6529c4764cd0">

- 콘텐츠 분할 요소 (div)
  - `<div>` : 가장 흔히 사용되는 레이아웃 태그로 단순히 구역을 나누기 위한 태그
- 레이아웃 태그 (header, footer, main)
  - `<header>` : 블로그 글 제목, 작성일 등의 주요 정보를 담는 태그 - 중복해서 사용 가능
  - `<footer>` : 페이지의 바닥줄에 사용되며, 저작권 정보, 연락처 등 부차적인 정보를 담는 태그 - 중복해서 사용 가능
  - `<main>` : 페이지의 가장 큰 부분으로 사이트의 내용 즉, 주요 콘텐츠를 담는 태그 - 한 페이지에 한번만 나와야 함
- 레이아웃 태그 (section, article, aside)
  - `<section>` : 콘텐츠의 구역을 나누는 태그로, 신문지에서 여러 기사가 각자의 구역에서 각자의 정보를 전달하는 의미와 비슷한 역할을 하는 태그
  - `<article>` : 블로그 포스트, 뉴스 기사와 같은 독립적인 문서를 전달하는 태그
  - `<aside>` : 문서의 주요 내용에 간접적인 정보를 전달하는 태그

> 레이아웃 태그를 알아야 하는 이유?
> : HTML5 부터 태그를 의미있게 사용하기 위해 “Semantic(시맨틱)” 태그를 사용하여 문서 구조를 작성, 단순히 의미 구분자인 <div> 를 남발하지 않고 적절한 태그를 사용하여 웹 문서가 담은 정보와 구조를 의미있게 전달, 시맨틱하게 마크업을 함으로써 검색엔진의 검색 순위에 가산점을 얻거나 홈페이지의 로딩 속도를 높임

---

Reference : [https://tcpschool.com/html/html_space_layouts](https://tcpschool.com/html/html_space_layouts)

## [Feelings+Finding]

- 이번 강의를 수강하기 전에 HTML 코드를 작성할때 Semantic 태그를 잘 사용하지 않았는데, 강의를 수강하고 나서 레이아웃 태그의 중요성을 깨달았고 문서의 구조를 잘 생각해보면서 레이아웃 태그를 제대로 사용해야겠다는 생각이 들었다.
