---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(12/22)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 12월 22일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til5

toc: true
toc_sticky: true

date: 2023-12-22
last_modified_at: 2023-12-22
---

## [Facts]

- CSS 에서 박스모델, flexbox, position,grid를 공부하였다

## [TIL]

### 박스모델 - 크기 지정, 여백

- **크기지정**
  - width, height : 박스의 너비, 높이를 지정할 수 있다
    - 블록 레벨 요소에서 사용할 수 있다
    - auto값을 사용해 브라우저가 값을 계산해 지정하게 할 수 있다
- **최대/최소 크기 지정**
  - max-width, max-height : 박스의 최대 너비, 최대 높이를 지정할 수 있다.
    - width, height 과 동일하게 블록레벨 요소에서 사용할 수 있다.
    - auto값을 사용해 브라우저가 값을 계산해 지정하게 할 수 있다.
- **외부/내부 여백**
  - margin, padding: 박스의 외부, 내부 여백을 지정할 수 있다
    - 블록 레벨 요소에서 사용할 수 있다.
    - 인라인 레벨 요소에서는 **좌/우에만 적용할 수 있다**
    - 네 방향의 여백을 지정할 수 있다.
    - 작성값의 갯수 따라 지정되는 방향이 다르다
    - margin은 음수 값의 적용이 가능하다
    ```css
    margin: 15px 10px 20px; /* 상 좌우 하 */
    ```
  - margin, padding / top right bottom left: 박스의 외부, 내부 여백을 지정할 수 있다.
    - 각 방향의 여백을 지정할 수 있다.
    - top, right, bottom, left 를 별개로 정의할 수 있다
- 여백 (마진) 상쇄 : 경우에 따라 요소 간의 외부 여백이 상쇄(결합)되는 현상이다
  - 인접 형제 간의 외부 여백은 상쇄된다
  - 제일 큰 여백을 따라 간다
  - 부모와 자식 요소의 여백을 분리할 권한이 없을 경우 상쇄가 발생한다.
    - 부모와 자식을 분리하는 방법 **(부모에 테두리 넣기, 부모와 자식 사이에 컨텐츠 넣기, 부모에 내부 여백 넣기)**
  - 빈 블록은 상쇄가 발생한다: 테두리, 여백, 콘텐츠, 높이가 없는 빈 블록은 마진 상쇄가 발생한다

### 박스 모델 - 테두리, 박스 크기

- 테두리
  - border: 박스의 네면에 테두리를 그릴 수 있다.
    - color, style, width를 사용해 박스의 테두리를 그릴 수 있다 : 각 속성은 top, right, bottom, left 값을 개별로 줄 수 있다
    - border-color: css color 값을 사용해 지정
    - border-style: solid, dotted를 가장 일반적으로 사용한다
    - border-width: 선의 두께를 지정할 수 있다.
    ```css
    border-left-style: dashed;
    ```
    ```css
    div {
      width: 100px;
      padding: 10px;
      border: 1px solid yellow;
    }
    /* 100px은 콘텐츠 크기!!! */
    ```
- 박스 크기 계산 방식
  - **_box-sizing : 박스 크기를 계산할때 내부 여백, 테두리의 크기를 포함할지 결정한다._**
    - 기본값은 content-box로 padding, width/height, border-width의 크기가 모두 더해진다
    - 값을 **_border-box_**로 설정하면 width/height 값안에 padding, border의 크기가 합해진다
    ```css
    div {
      box-sizing: border-box;
    }
    ```

### 박스 모델 - 초과, 투명도

- 초과
  - **overflow**: 콘텐츠 내용이 지정한 박스 크기를 초과했을때를 대처한다
    - 기본값은 visible로 초과해도 내용이 그대로 노출된다
    - overflow-x, overflow-y로 분리해서 지정할 수 있다
    - 적용가능한 값
      - visible(기본값): 그대로 노출
      - hidden: 숨김
      - scroll: 스크롤바 무조건 노출
      - auto: 브라우저가 자동으로 결정하여 스크롤바 노출
- 투명도
  - **opacity:** 박스의 투명도를 조절한다
    - 기본값은 1이며, 0~1사이 소수점을 사용해 적용 가능하다
    - 투명도가 적용되면 자식 요소도 함께 투명해진다
    - **_opacity의 값은 상속되지 않는다_**

### 표시유형과 레이아웃 - 표시유형, flex, position

- 표시유형
  - display: 요소를 블록, 인라인에 대한 처리의 선택과 자식 요소를 배치하는 레이아웃을 설정할 수 있다
    - 태그마다 가진 기본값이 있다
    - span, strong 같은 인라인 태그의 display 유형을 block으로 변경하여 블록 레벨 요소에서 사용할 수 있는 css를 적용할 수 도 있다.(문단 태그도 블록 레벨 요소)
    - 반대로 블록 레벨 요소의 display 유형을 inline으로 변경하여 문맥의 흐름에 포함시킬 수 있다
    ```css
    span {
      display: inline-block;
    }
    /* 문맥의 흐름도 inline처럼 유지하고 block이 가진 css도 사용할 수 있음 */
    ```
    - **none**값을 사용하여 요소가 존재하지 않는 것 처럼 처리 할 수 있다
      - none으로 사라진 요소는 접근성 트리에서 제외되기 때문에 스크린 리더가 읽지 않는다
  - visibility: 레이아웃을 변경하지 않고 시각적으로 보이거나 숨길 수 있다
    - display의 none과 다르게 시각적으로만 숨겨지기 때문에 레이아웃상에서 공간을 그대로 차지하게 된다
    - hidden으로 숨겨진 요소는 접근성 트리에서 제외되기때문에 스크린 리더가 읽지 않는다
- float : 문맥의 흐름으로부터 빠져 좌우측에 배치되는 속성이다

  - MS Word나, 한글 문서에서 이미지를 좌측, 우측에 배치하는 속성이다.
  - left, right로 배치할 수 있다

  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Document</title>
      <link rel="stylesheet" href="style.css" />
    </head>
    <body>
      <img src="#" />
      <p>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Assumenda
        aliquid ex maiores! Dolorum esse ut temporibus laboriosam aperiam. Ad
        sunt vitae nobis sed magni ipsa itaque quod aliquid facere quibusdam?
      </p>
      <!-- 이미지 태그와 p 태그 위 아래가 바뀌면 안된다. 문맥의 흐름은 위에서 아래로 흘러가기 때문 -->
    </body>
  </html>
  ```

  ```css
  img {
    float: left;
  }
  ```

- **position**: 문서상에 요소를 배치하는 방법을 지정한다
  - top, right, bottom, left 값으로 offset(위치)을 제어할 수 있다
  - z-index 값으로 z축을 제어해 쌓이는 순서를 정의할 수 있다
  - 적용 가능 값
    - static(기본값): 문서의 흐름에 따라 배치되고 offset 및 z-index를 제어할 수 없다
    - relative: 문서 흐름에 따라 배치하고 현재 위치 기준으로 offset과 z-index를 제어한다
    ```css
    .box{
    	position: relative
    	top: 15px;
    	left: 10px;
    }
    ```
    - absolute: 문서흐름에서 제거하고 가장 가까운 위치의 relative 요소에 상대적으로 배치된다(가장 가까운 relative 부모를 기준으로 이동)
    - fixed: 문서 흐름에서 제거하고 브라우저의 화면 기준으로 배치된다(element가 처음 생성된 자리에 고정)
    - sticky: 문서 흐름에 따라 배치되나, 요소가 스크롤에 닿으면 따라다닌다

### 표시 유형과 레이아웃 - Flexbox, Grid

- 유연한 상자 만들기(Flexbox) : 유연함을 가진 일차원 레이아웃을 만들 수 있다
  - **가로축 정렬: justify-content - (flex-start, flex-end, space-between, space-around, space-evenly, center)**
  - **세로축 정렬: align-items - (stretch, flex-start, flex-end, center, baseline)**
  - 유연성 조절: flex-grow, flex-shrink
  - 크기 조절: flex-basis
    - ( flex: 0 0 auto ← 이런식으로, flex-grow, flex-shirink, flex-basis 한번에 쓸 수 도 있음)
  - **축 바꾸기: flex-direction (**`flex-direction: column`을 주면 주축과 교차축이 반전된다.)
  - 여백과 순서: gap(콘텐츠 사이끼리 gap을 준다), order(원하는 순서에 맞게 정렬을 할 수 있음, 마크업 순서는 변하지 않음)
  - flex-wrap: nowrap을 통해 wrapping이 일어나지 않게 할 수 있다.
  - 참고: [https://flexboxfroggy.com/#ko](https://flexboxfroggy.com/#ko)
- 바둑판 상자 만들기(Grid) : 수평선과 수직선을 가진 2차원 레이아웃을 만들 수 있다

  - 바둑판 조절하기 : grid-template
    ```css
    .box {
      display: grid;
      grid-template-columns: repeat(10, 30px);
      /* 30px짜리 10개 열*/
    }
    .box2 {
      display: grid;
      grid-template: repeat(2, 100px) / repeat(5, 50px);
    }
    ```
  - 반복하기 : repeat
  - 셀 확장 : grid-row, grid-column

  ```css
  .box{
    grid-column: 1 / 3
    /* 칸을 두 칸 차지해야 할 것 에게 어디까지 가라고 말해야함. 위치가 바뀔 수 있을 때 안좋으니까 span을 사용하는 편이 좋음.*/
    grid-column: span 2;
    /* column 한 셀을 2칸을 차지해라. */
    grid-row: span 2;
    /* row를 두칸을 차지해라. */

    grid-column: 3;
    grid-row: 1 / 3;
    /* 일단 번호를 해준 후.이렇게 2셀을 차지하게 만들어주면 2칸 차지가능 */
    /* 칸이 병합되었을 때, 위치가 병합된 칸으로 가라고 했을 때에는, 병합된 칸을 밀어내고 그냥 칸으로 감. */}
  ```

  - 영역 지정하고 배치하기 : grid-templte-areas, grid-area

  ```css
  .box {
    display: grid;
    grid-template-areas:
      "header slider slider"
      "header content content"
      "header footer banner";
  }
  .box2 {
    grid-area: header; /* 지어진 이름으로 가라라는 뜻. 따옴표로 감싸면 안됨 */
  }
  ```

  - 여백과 순서 : gap, order

### CSS 주의 사항

- 클래스명을 사용할 때, 대소문자 주의. 숫자부터 시작하면 안됨
- 한글 금지
- 결합을 할 때, 계층 주의해서 확인
- 마크업 순서와 css 순서가 같아야 좋음

## [Feelings+Finding]

- grid로 수평선과 수직선을 가진 2차원 레이아웃을 만들 수 있다. grid에 대해서 공부할 때 grid는 시작 라인과 끝 라인을 지정하여 이 라인에 따라 콘텐츠들을 정렬할 수 있는데 이 부분이 살짝 헷갈렸다. 실습을 통해서 완전히 체득해야겠다. 파이팅 :)

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
