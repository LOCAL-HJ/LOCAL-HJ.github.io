---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(12/20)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 12월 20일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til3

toc: true
toc_sticky: true

date: 2023-12-20
last_modified_at: 2023-12-20
---

## [Facts]

- 3일차 강의 수강

## [TIL]

### 콘텐츠

- **제목 태그**
  - `<h1>` ~ `<h6>` : 문서 구획 제목을 나타내는 태그로 Heading 태그라고 부른다.
  - `h1` 태그는 페이지 내에 한번만 사용되어야 하고 구획의 순서는 지켜져야 한다.
  - 잘못 구성된 구획의 순서 예시
    ```html
    <h1>제목</h1>
    <h2>제목</h2>
    <h3>제목</h3>
    <h6>제목</h6>
    <h3>제목</h3>
    <h5>제목</h5>
    ```
- **문단 태그**
  - `<p>` : 문서에서 하나의 문단을 나타내는 태그
    - 제목 태그와 함께 사용되기도 하고 단독으로 사용되기도 함
    - 블록레벨요소
    - **문단 태그이기 때문에 레이아웃 태그처럼 사용하면 안된다**
- **서식 태그**
  - `<b>`, `<strong>`: 글씨의 두께를 조절할 수 있음
    - `<b>` 태그는 의미를 가지지 않고 단순히 굵은 글씨로 변경만 해준다
    - `<strong>` 태그는 굵은 글씨로 변경후 강조의 의미를 부여한다
    - `<b>`와 `<strong>`은 시각적으로 굵은 효과는 같지만 의미가 다름으로 사용에 주의하자!
  - `<i>`, `<em>`
    - 글씨의 기울기를 조절할 수 있다
    - `<i>` 태그는 기울임과 동시에 텍스트가 문단의 내용과 구분 되어야 하는 경우 사용할 수 있다. (예를 들어, 등장인물, 외국어 구절, 기술용어 등), 부가적인 정보를 나타냄
    - `<em>` 태그는 기울임과 내용에 강조를 나타낸다
    - `<i>`와 `<em>`은 시각적으로 기울임은 같지만 의미가 다름으로 사용에 주의하자!
    - _cf. `<br>` 태그는 단일 태그로 줄바꿈을 해줌_
  - `<u>`
    - 글씨에 밑줄을 넣고 주석을 가지는 단어임을 나타낼 수 있다
      - CSS로 스타일링 하여 빨간 밑줄을 넣는 것으로 오타를 나타내는 것처럼 사용할 수 있다.
      - 단순하게 밑줄만 긋는 용도로 사용하면 안된다.
  - `<s>`, `<del>`
    - 글씨에 취소선을 추가할 수 있다.
    - `<s>` 태그는 단순히 시각적인 취소선만 추가되고 접근성 기기에 취소에 대한 안내는 하지 않는다.
    - `<del>` 태그는 문서에서 제거된 텍스트를 나타낼 수 있다. `<ins>` 태그를 함께 사용하면 제거된 텍스트 옆에 추가된 텍스트를 표현할 수 있다.
  ```html
  <em>기울어짐</em> <br /><br /><br />
  <strong>띄어쓰기했다</strong>
  <strong><u>밑줄도 긋고 강조도 한다</u></strong>
  <del>삭제</del><ins>추가</ins>
  ```
- **링크 이동**
  - `<a>`
    - 클릭하면 페이지를 이동할 수 있는 링크 요소를 만들 수 있음
    - **href 속성**을 사용해서 이동하고자 하는 파일 혹은 URL을 작성
    - **target속성**을 사용해서 이동해야할 링크를 새창, 현재창 등 원하는 타겟을 지정할 수 있음
    ```html
    <a href="https://www.naver.com" target="_blank">네이버로 가기</a>
    ```
- **멀티미디어**
  - `<img>` : 문서내에 이미지를 넣을 수 있는 태그
    - **src** 속성을 사용해 이미지의 경로를 넣으면 이미지가 출력됨
    - **alt** 속성을 사용해 이미지 로딩에 문제가 발생했을때 대체 텍스트를 띄울 수 있음
  - `<figure>`, `<figcaption>` : 하나의 독립적인 콘텐츠로 분리하고 그에 대한 설명을 넣을 수 있는 태그
    - `<figcation>` 태그를 사용해 콘텐츠의 설명 혹은 범례를 추가할 수 있고 제일 처음이나 제일 아래에 추가해서 사용할 수 있다.
    - **_figcation은 줄이 여러개 있을때 중간에 들어가는건 안된다_**
    - 보통 이미지를 넣는데 인용문, 비디오/오디오 등 문서의 흐름에 참조는 되지만 독립적으로 분리되어도 되는 내용을 담을 수 있다.
      ```html
      <figure>
        <img src="/dog.png" alt="강아지" />
        <figcaption>귀여운 강아지</figcaption>
      </figure>
      ```
  - `<video>` : 문서 내에 영상을 첨부할 수 있는 태그
    - src 속성을 사용하여 비디오를 문서 내에 첨부할 수 있음
    - poster 속성을 사용하면 비디오가 로드되기 전에 포스터를 보여줄 수 있다.
    - `<source>` 태그를 사용하면 여러 타입의 비디오를 제공할 수 있다.
      ```html
      <video>
        <source src="" type="" />
        <source src="" type="" />
      </video>
      ```
  - `<audio>` : 문서 내에 소리를 첨부할 수 있는 태그
    - **src** 속성을 사용하여 소리를 문서내에 첨부할 수 있다.
    - `<source>` 태그를 사용하면 여러타입의 비디오를 제공할 수 있다.
    - **controls** 속성을 사용하면 재생/정지 버튼 등이 있는 컨트롤러를 띄울 수 있다
      ```html
      <audio controls src=""></audio>
      ```
  - `<svg>` (Scalable Vector Graphics) : 그래픽으로 만들어진 이미지
    - 일반 이미지(래스터 이미지)와 다르게 수학 공식을 사용하여 그려지기 때문에 해상도의 영향을 받지 않아 확대/축소가 자유롭다
    - 주로 크기를 자주 바꾸어야하는 작은 아이콘에서 많이 사용된다
    - 해상도가 다양하게 변화하는 최근 기기들로 인해 아이콘 외에 로고 등 주요 이미지에도 사용되고 있다.
    - `<img>` 태그처럼 svg파일을 불러올 수도 있고 태그를 그대로 사용할 수 있다(더많은 사용 방식 존재)
      ```html
      <img
        width="100"
        height="100"
        src="assets/cat.svg"
        alt="고양이 아이콘svg"
      />
      ```
    - 코드로 이루어져있기 때문에 스타일을 변경하거나 자바스크립트를 사용해 간단한 기능을 추가할 수 도 있다.
- **리스트**
  - `<ul>`, `<li>` : 정렬되지 않은 목록 태그
    - 기본 불릿(bullet) 형식으로 목록을 그린다.
    - `<li>` 태그를 사용하여 목록을 구성할 수 있고 다양한 태그를 포함 할 수 있다.
    - `<ul>` 태그의 자식 요소로는 `<li>` 태그만 들어와야 한다. 하위 리스트를 만들려면 `<li>`태그 안에 `<ul>`, `<ol>` 태그를 사용하면 된다.
  - `<ol>`, `<li>`: 정렬된 목록 태그
    - 기본 숫자 형식으로 목록을 그린다
    - `<li>` 태그를 사용하여 목록을 구성할 수 있고 다양한 태그를 포함 할 수 있다.
    - `<ol>` 태그의 자식 요소로는 `<li>` 태그만 들어와야 한다. 하위 리스트를 만들려면 `<li>` 태그안에 `<ol>`, `<ul>` 태그를 사용하면 된다.
      ```html
      <ul>
        베스킨라빈스 Menu
        <li>
          아이스크림
          <ol>
            <li>사랑에 빠진 딸기</li>
            <li>엄마는 외계인</li>
          </ol>
        </li>
        <li>
          커피
          <ol>
            <li>아메리카노</li>
            <li>카페라떼</li>
          </ol>
        </li>
      </ul>
      ```
  - `<dl>`, `<dt>`, `<dd>` : 설명 목록 태그
    - `<dt>` 태그에 사용된 단어 혹은 내용의 설명은 `<dd>` 태그에 작성할 수 있다.
    - 주로 용어 사전이나 “키-값” 이 있는 쌍의 목록을 나타낼 때 사용한다
    - `<dt>` 태그를 여러개 작성하고 하나의 `<dd>` 태그를 작성하는 것으로 여러 개의 용어를 설명할 수 있다.
    - 위와 반대로, `<dt>` 태그 하나에 여러개의 `<dd>` 태그를 가질 수 있다.
      ```html
      <dl>
        <dt>사과</dt>
        <dd>빨간 과일이다.</dd>
        <dd>영어로는 Apple</dd>
      </dl>
      ```
- **표**
  - `<table>` : 표를 만드는 태그
    - `<tr>`태그로 행을 구분할 수 있다. (보통 row라고 부른다)
    - `<td>`태그로 열을 생성할 수 있다.(보통 cell 이라고 부른다)
    - `<th>` : 열 제목 태그 - `<th>` 태그를 사용하면 셀의 제목을 만들 수 있다.
    - `<thead>` : 제목 그룹태그 - `<thead>` 태그안에 열제목의 행을 넣음로써 그룹을 지을 수 있다.
    - `<tbody>` : 표 본문 요소 태그 - `<tbody>` 태그 안에 여러 열의 행을 넣음으로써 본문 요소를 그룹지을 수 있다.
    - `<tfoot>` : 표 바닥글 요소 태그 -`<tfoot>`태그안에 여러 열의 행을 넣음으로써 표의 바닥글 요소를 넣을 수 있다. 문서버전이 HTML4라면 `<tfoot>`는 `<tbody>`보다 먼저 작성되어야 하고 HTML5버전이라면 `<thead>`, `<tbody>`, `<tfoot>` 순으로 배치되어야 한다.
    - `<caption>` : 표 설명 태그 - `<caption>` 태그를 사용하여 표가 가진 데이터에 대한 설명을 넣을 수 있다.
      ```html
      <table>
        <thead>
          <tr>
            <th>이름</th>
            <th>ID</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>제니</td>
            <td>1</td>
          </tr>
          <tr>
            <td>지수</td>
            <td>2</td>
          </tr>
          <tr>
            <td>로제</td>
            <td>3</td>
          </tr>
          <tr>
            <td>리사</td>
            <td>4</td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td>마지막 멤버</td>
            <td>5</td>
          </tr>
        </tfoot>
      </table>
      ```
- **외부 콘텐츠**

  - `<iframe>` : 현재 문서 안에 다른 HTML 페이지를 삽입할 수 있는 태그

    - src 속성에 원하는 HTML 문서 또는 URL을 넣을 수 있다.
    - 외부 페이지를 불러올 수 있기 때문에 불러온 외부 페이지의 영향을 받을 수 있다.
    - name 속성을 지정하면,`<a>` 태그의 target 속성을 사용해 iframe에서 문서 또는 URL 이 열리게 할 수 있다.

      ```html
      <iframe src="/example01/index.html">아이프레임 지원할 수 없음 </iframe>
      ```

      ```html
      <iframe name="sample" src="https://example.com/"></iframe>
      <a href="index.html" target="sample">예시</a>
      <!-- 우리 링크를 iframe 사용해서 불러올 수도 있다-->
      ```

### 양식 태그

- `<form>` : 정보를 제출하기 위한 태그

  - 정보를 입력하고 선택할 수 있는 **input, selectbox, textarea** 등을 가질 수 있다.
  - 정보를 제출하기 위한 **button**을 가진다.
  - **_action_** 속성으로 정보가 제출되었을때 페이지를 이동시킬 수 있다.
  - **_method_** 속성으로 정보가 제출될때 처리 방식을 결정할 수 있다.
    - get: 주로 검색할 때 (검색어가 도메인 뒤에 붙게)
    - post: 로그인할 때 ( 보안이 중요할 때)
  - form 태그 안의 button 태그의 기본 타입은 submit

  ```html
  <!-- example01.html -->
  <form action="/practice/example02.html" method="get">
    <input type="text" placeholder="이름을 입력하시오" />
    <input type="number" placeholder="나이를 입력하시오" />
    <select>
      <option>대학생</option>
      <option>고등학생</option>
      <option>중학생</option>
    </select>
    <button type="submit">제출하기</button>
  </form>
  ```

  ```html
  <!-- example02.html -->
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Document</title>
    </head>
    <body>
      <h1>제출 완료! 페이지 이동 중</h1>
    </body>
  </html>
  ```

    <img width="469" alt="1" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/f5d90710-618b-4738-b522-28352de37d56">

    <img width="471" alt="2" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/8f3b1d49-65da-46f0-87ac-6e4dcde1eaa2">

- `<label>`**: input , textarea, selectbox** 의 설명을 작성할 수 있는 태그

  - **_for_** 속성을 사용하여 연결하고자 하는 태그에 id 속성을 지정하면 label을 클릭하면 연결된 태그가 선택된다
  - label 태그 안에 input을 넣으면 자동으로 for → id 연결과 같은 처리를 해준다
  - id 속성은 값이 절대로 중복되면 안된다

  ```html
  <label for="name">이름 : </label>
  <input id="name" type="text" />

  <!-- 아래 처럼 작성해도 된다 -->

  <label>
    나이 :
    <input name="age" type="number" />
  </label>
  ```

- `<input>`: 사용자에게 데이터를 입력받을 수 있는 대화형 태그

  - **type** 속성의 값에 따라 받을 수 있는 input의 유형이 달라진다. (기본값: text)
  - **value** 속성을 사용해 기본 내용을 입력 해둘 수 잇다.
  - **name** 속성을 사용해 input의 이름을 지정할 수 있다.
  - 자주 사용되는 input 타입

    1. checkbox : input을 체크 박스 형태로 만든다
    2. radio : 라디오 버튼으로 만든다.

       ```html
       <input type="radio" name="number" value="1" />불만족
       <input type="radio" name="number" value="2" />보통
       <input type="radio" name="number" value="3" />만족
       ```

       <img width="496" alt="3" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/afe536de-e90e-4653-ad02-40ae0acb2405">

    3. file : 파일을 첨부할 수 있게 만든다.
    4. button : value 속성에 입력된 값을 이름으로 갖는 버튼으로 만든다 (버튼 태그는 submit이 기본 타입임 그래서 전송이 되는데 input은 전송이 안됨)
    5. hidden : input을 시각적으로 숨겨준다. 정보 제출시 value 속성에 입력된 값은 전송된다.

       ```html
       <input type="hidden" name="hiddentype" value="숨겨짐" />
       ```

       <img width="436" alt="4" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/6744a418-022a-4fb2-bd2b-17cb2fad3297">

- `<select>` : 옵션 메뉴를 제공하는 태그
  - `<option>`태그를 사용해 옵션을 정의할 수 있다.
  - 첫번째 option은 이름이 된다.
  - **_value 속성을 선언하지 않은 경우 `<option>`태그의 콘텐츠가 기본값이 된다._**
  - 흔히 셀렉트박스라고 불리워진다.
  - 첫번째 옵션이 버튼명이기 때문에 placeholder 속성을 사용할 수 없다.
  ```html
  <label for="option">학교</label>
  <select id="option" name="school" required>
    <option value="">현재 재학 중인 학교를 선택하세요</option>
    <!-- 아무것도 전송이 안되게 하기 위해서 value가 비어 있는 것을 일부러 만들어줌 -->
    <option value="university">대학교</option>
    <option value="highschool">고등학교</option>
    <option value="middleschool">중학교</option>
  </select>
  <button>제출하기</button>
  <!-- 위 코드에서 아무것도 선택 안하고 제출시 required 때문에 창이 넘어가지 않음 -->
  ```
    <img width="434" alt="5" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/c3015b39-a833-413f-bb53-50f2b154c2e2">
- `<textarea>` : 여러 줄을 입력할 수 있는 대화형 태그
  - 콘텐츠를 넣으면 사용자가 입력하지 않아도 표시되는 기본값이 된다.
  - cols/rows 속성으로 기본 너비와 높이를 지정할 수 있다. 너비와 높이는 글자 크기 기준으로 정의된다. (cols: 가로 너비, rows: 세로 너비)
- 알아두면 좋은 속성
  - **_readonly:_** 사용자가 수정할 수 없는 읽기 전용으로 만든다. _(value 값으로 고정으로 적어놓을 수 있음)_
  - **_required_**: form이 제출될때 필수 입력사항으로 만든다. 이때 필수입력에 대한 태그에 따른 안내 문구, 행동 등은 브라우저가 자동으로 처리해준다.
  - **_placeholder_**: input, textarea에 부가 설명을 입력해둘 수 있다. `<select>`태그에선 사용할 수 없다.
  - **_disabled_**: 요소가 비활성화 되며 정보 제출시 값이 제출되지 않는다.
- `<button>` : 클릭 가능한 버튼을 태그로 `<form>` 태그 내에서 어디서든 사용할 수 있다.
  - type을 reset으로 지정하면 버튼이 눌리면 입력한 양식이 모두 초기화된다
  - type을 submit으로 지정하면 form 양식을 제출할 수 있다. `<form>` 태그내 `<button>` 태그의 기본 type은 submit이다.
  - `<button>` 태그내 콘텐츠에 태그의 입력이 가능하나, 블록 레벨 태그는 사용하면 안된다.
  - **disabled** 속성을 가질 수 있다.

### HTML 주의 사항

- 대 소문자 주의 : 태그는 가능한 소문자로 작성
- 닫는 태그 생략 주의
- 한글 사용 - 개발은 영어로
- ID의 중복: ID는 한 문서, 한 페이지 내에 한번만 나와야하는 고유아이디 이다
- 계층 구조 유지
- 동일한 의미의 태그 중첩 금지 : 예) b 태그와 strong 태그, a태그와 button 태그 등

### 추천 사이트

1. TCP School
2. MDN
3. W3School

## [Feelings+Finding]

- Html 을 예전에 공부한적이 있었지만 이번 강의를 수강하면서 더 많은 태그를 새롭게 알게 되었으며, value 속성과 name 속성에 대해서 새롭게 알게 되어서 좋았다.
