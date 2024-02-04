---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/2)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 2일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til6

toc: true
toc_sticky: true

date: 2024-1-2
last_modified_at: 2024-1-2
---

## [Facts]

- 반응형, End 공부

## [TIL]

- 반응형: 하나의 웹사이트에서 PC, Tablet, Mobile 등 접속하는 기기의 화면 크기에 맞게 사이트가 자동으로 반응하는 기법
- 적응형: 접속하는 기기에 따라 pc용 웹사이트, 테블릿/모바일 용 웹사이트를 보여주는 기법

### HTML

- 반응형 페이지를 만들기 위한 메타 태그 : viewport meta 태그를 추가하여 페이지가 호출이 될때 보이는 화면을 어떻게 계산해서 보여줄지 정의 할 수 있다.

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  ```

  - name: 메타태그 중 viewport를 사용하겠다고 선언
  - content: viewport가 가진 content값을 지정하여 사용
    - width: 브라우저에게 페이지의 가로 너비를 계산하는 방법을 알려주며 device-width를 지정하면 접속하는 기기의 브라우저 너비에 맞게 페이지를 맞춰준다
    - initial-scale: 최초 화면 확대 값으로, 1.0을 두는 것으로 페이지를 확대하지 않고 1배율로 보겠다고 정의한다

- 반응형 이미지 처리 : picture 태그를 사용하여 의도한 viewport 너비에 원하는 이미지를 넣을 수 있다.
  ```html
  <picture>
    <source media="(max-width:765px)" srcset="#" />
    <!-- 최대 가로 너비가 765px이하일때 이 이미지(모바일이미지)를 사용하겠다 -->
    <img src="#" alt="pc용 이미지" />
  </picture>
  ```

### CSS

- 미디어 쿼리 (Media Query) : 기기의 유형과, 어떤 특성이나 수치에 따라 스타일을 수정할 수 있다.
  - @media 로 시작한다
  - 기기 유형 : all-모든장치, print-인쇄 결과물 및 출력 미리보기, screen-화면
  - 규칙 : 뷰포트너비(가장 많이 사용), 뷰포트의 가로세로비 등등
  - and 연산자를 통해 조건을 계속 추가할 수도있음
  - 조건은 괄호로 감싸야한다
  ```css
  @media 기기유형 연산자 (조건){
      콘텐츠
  }
  /* 기기유형에 screen, print, all 이 있음 (바로 조건을 넣을 수도 있음) */
  ```
  ```css
  div {
    font-size: 20px;
    background-color: yellowgreen;
  }
  @media screen and (max-width: 1000px) {
    div {
      background-color: yellow;
    }
  }
  ```
  ```css
  @media screen and (min-width: 500px) and (max-width: 1000px) {
    /* 500px이상 1000px이하인 구간에서 적용 */
  }
  ```
- CSS 호출 방법: link 태그를 사용하면 원하는 유형과 조건에 따라 스타일 파일을 불러올수 있다
  ```css
  <link rel="stylesheet" href="style.css" media="print">
  <link rel="stylesheet" href="style2.css" media="screen and (max-width: 500px)">
  ```
- 주의사항
  1. 레이아웃의 고정 크기의 사용 지양
     - width 값을 고정하면 반응형 매구간마다 고정값을 변경해야하는 불편함이 발생할 수 있다. max-width를 사용한 최대 너비 적극 활용
     - height 값을 고정하면 유동적으로 변하는 높이에 대응할 수 없다. min-height를 사용한 최소 높이를 적극 활용
  2. 인라인 스타일은 반응형을 처리할 수 없다.
     - 태그에 style 속성으로 직접 들어간 인라인 css는 미디어 쿼리를 적용할 수 없다.

### END

[https://caniuse.com/](https://caniuse.com/) : 어떤 버전 지원하는지 알 수 있음

## [Feelings+Finding]

- 반응형 웹페이지를 구현할때 HTML에서는 viewport meta 태그를 추가하여 구현할 수 있으며 CSS에서는 미디어 쿼리를 이용하여 구현할 수 있다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
