---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(12/21)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 12월 21일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til4

toc: true
toc_sticky: true

date: 2023-12-21
last_modified_at: 2023-12-21
---

## [Facts]

- 4일차 강의 수강

## [TIL]

### CSS

- CSS (Cascading Style Sheets) : 웹 문서를 꾸미기 위한 Style Sheet 언어
- 기본 문법
  ```css
  div {
    font-size: 20px;
    letter-spacing: 10px;
  }
  ```
- 속성과 값 : font-size : 속성, 20px: 값
- 내부 CSS : 웹 문서 안에서 스타일을 작성
  - `<head>` 태그 안에 `<style>` 태그를 사용하여 작성
  - HTML5 부터 type 속성의 선언은 생략 가능

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      h1 {
        color: blue;
      }
    </style>
  </head>
  <body>
    <h1>programmers</h1>
    <div>데브코스</div>
  </body>
</html>
```

- 외부 CSS : 별도의 파일을 만들어서 스타일 코드 관리
  - 스타일이 길어질 경우 하나의 문서내에서 관리할 수 없기 때문에 분리해서 관리를 하기 위함
  - href 속성에 분리한 스타일 시트의 경로를 입력하여 사용
  - rel 속성에 stylesheet를 넣어 스타일 시트 파일을 불러 오는 것을 정확히 명시

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
    <h1>programmers</h1>
    <div>데브코스</div>
  </body>
</html>
```

```css
h1 {
  color: yellow;
}
div {
  font-size: 80px;
  letter-spacing: 50px;
}
/* css 주석 입니당 */
```

- inline CSS : 태그에 직접 스타일 정의
  - 전역 속성인 style 속성을 사용하여 스타일을 선언 할 수 있음
  - 코드 유지보수의 어려움, 반응형 처리 불가능 등의 이유로 가능한 사용을 지양해야함

```html
<p style="color: orange; font-size: 50px">css 실습 중</p>
```

- CSS 주석 : 스타일 시트 내에 개발자가 남기는 코멘트
  - /\*\*/ 사이에 내용을 입력할 수 있다
  - 줄바꿈을 통해 여러 줄의 주석을 남길 수 있다
  - 주석 안에 주석은 작성할 수 없다

### 선택자, 상속과 초기화

- **전체 선택자 (\*)** : 모든 요소에 스타일을 적용할 수 있는 선택자
  - 웹 문서 내의 모든 요소에 스타일이 적용된다
- **유형 (태그) 선택자** : HTML 태그 이름으로 선택한다.
  - 같은 이름의 태그를 모두 선택한다
- **ID, Class 선택자 :** 요소의 id, class 속성 값에 완전히 동일한 값을 가진 요소를 선택한다.
  - ID: # 을 시작으로 선택한다(ID 값은 중복되면 안된다)
  - Class: . 을 시작으로 선택한다
- **속성 선택자** : 요소가 가진 속성을 선택자로 한다.
  - 대괄호 “[]” 안에 속성 이름을 넣어 선택자로 사용할 수 있다.
  - 속성과 값을 동시에 입력하면 값까지 동일한 요소를 선택할 수 있다.
  - 대괄호 앞에 태그명을 붙이면 좀 더 강력하게 선택자를 제한할 수 있다.
    - ex) a[href]
- **의사(가상) 클래스** : 기존 선택자에 추가하는 특별한 상태를 선택하는 선택자
  - 대표적인 의사(가상) 클래스
    - 마우스를 올리면 적용되는 “:hover”
    - 키보드의 Tab 키로 이동시 focus 되는 “:focus”
    - 리스트의 첫번째 요소만 선택하는 “:first-child”
    - n번째 요소를 선택하는 “:nth-child(n)”
- **의사(가상) 요소** : 기존 선택자에 추가하는 선택한 요소의 일부를 스타일링하는 선택자
  - 대표적인 의사(가상) 요소
    - 요소의 앞에 의사 요소를 생성하는 “::before”
    - 요소의 뒤에 의사 요소를 생성하는 “::after”
    - `<input>` 태그의 “placeholder” 속성을 스타일링 하는 “::placeholder”

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
    <h1>programmers</h1>
    <div>데브코스</div>
    <a href="https://programmers.co.kr/">프로그래머스로 가기</a>
    <a href="https://naver.co.kr/">네이버로 가기</a>
    <a href="https://google.co.kr/" target="_blank">구글로 가기</a>
    <div id="mousehover">마우스를 글씨 위에 올려보세요.</div>
    <ul>
      <li>집</li>
      <li>학교</li>
      <li>직장</li>
    </ul>
  </body>
</html>
```

```css
h1 {
  color: yellow;
}
div {
  font-size: 30px;
  letter-spacing: 50px;
}
/* css 주석 입니당 */
a {
  color: orange;
}
[href="https://naver.co.kr/"]
{
  color: green;
}
a[target="_blank"] {
  color: cornflowerblue;
}
div:hover {
  letter-spacing: 0px;
  font-size: 100px;
}
ul li:first-child {
  color: rgb(47, 137, 137);
}
ul li:first-child::after {
  content: " 최고";
}
```

<img width="786" alt="스크린샷 2024-01-31 오후 10 57 23" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/f0136d3d-319c-4ceb-97de-6c631cce433f">

### 상속과 초기화

- 상속: 부모 요소의 스타일 값을 이어받아 자식 요소에 적용하는 것
  ```html
  <h3>제목</h3>
  <div>
    <h3>제목2</h3>
  </div>
  <!-- h3태그에 글씨색을 파란색으로 지정한다면, div태그 안에 있는 h3태그도 파란색으로 -->
  ```
  ```css
  h3 {
    color: blue;
  }
  div {
    color: yellow;
  }
  div h3 {
    color: inherit;
  }
  ```
  - CSS 셀렉터를 2개 이상 잡은 것을 **자손 결합자**라고 한다.
- 초기화: 브라우저가 지정한 속성의 초기값을 요소에 적용한다.
  ```html
  <p><em>프로그래머스</em></p>
  ```
  ```css
  p {
    color: blue;
  }
  em {
    color: initial;
  }
  ```
  - `em` 태그의 글자는 `p` 태그의 자식 요소이기 때문에 p 셀렉터에 선언한 color 속성으로 인해 파란색이 될 것 같지만, em 셀렉터에 선언된 **_initial_** 값으로 인해 브라우저가 지정한 초기값이 적용된다.
  ```css
  em {
    font-style: initial;
  }
  /* 기울임이 사라짐 */
  ```

### 결합자, 우선순위

- **자손결합자**: 한칸의 공백을 주어 앞 셀렉터의 자식 요소를 선택한다
  ```css
  div span {
    color: yellow;
  }
  ```
- **자식결합자**: 앞 셀렉터의 **직계 자식** 요소를 선택한다.
  ```css
  div > span {
    color: yellow;
  }
  ```
- **인접 형제 결합자**: 앞 셀렉터의 **바로 다음에 위치한 형제 요소**를 선택한다.
  ```css
  a + p {
    color: yellow;
  }
  /* a태그의 바로 다음 p태그의 글자에만 노란색이 적용된다 */
  ```
- **일반 형제 결합자**: 앞 셀렉터의 다음에 위치한 **모든 형제 요소**를 선택한다.
  ```css
  a ~ p {
    color: red;
  }
  ```
- **우선 순위 (명시도)** : 작성 순서, 결합, 선택자에 따라 우선 순위는 변경된다.

  - 기본 우선 순위 : 아래로 내려갈 수록 높은 우선 순위를 가진다.
    1. 유형(태그) 선택자 및 의사 (가상) 요소
    2. Class 선택자, 속성 선택자, 의사(가상) 클래스
    3. ID 선택자
    4. inline CSS

  ```html
  <div class="pro">프로그래머스 데브코스</div>
  ```

  ```css
  .pro {
    color: yellow;
  }
  div {
    color: blue;
  }
  /* 노란색 */
  ```

  - !important : 돌발 상황을 발생시키는 악동 ( 특정 Style의 우선순위를 먼저 가져올 수 있다)
    - important를 이기려면 더 많은 자손을 결합하고 important를 선언해야하는데, 잘못될 경우 important 지옥에 빠질 수 있으니 반드시 주의해야하고 important의 사용은 지양해야한다.
    ```css
    div {
      color: blue !important;
    }
    ```

### 단위

- **고정단위(px)** : Pixel (픽셀)은 정확한 크기를 나타내야할때 사용된다
  - 웹 문서에서 고정값을 나타낼때 가장 일반적으로 사용하는 단위
  - 보통 웹 브라우저의 기본 폰트 크기는 16px이다.
  - OS, 모니터, 기기성능 등에 따라 픽셀의 처리가 조금씩 다르기 때문에 소수점은 사용하지 않기를 권장
- **고정단위(pt)** : Point(포인트)는 일반적으로 문서 등에서 사용되는 단위이다.
  - 보통 웹 브라우저의 pt 단위 기본 폰트 크기는 12pt이다.
  - 픽셀과 마찬가지로 소수점은 사용하지 않기를 권장
- **상대 길이 단위 (em)**
  - em(이엠)은 요소의 글꼴 크기에 상대적인 단위이다.
  - 또한 em(이엠)은 합성 값이기도 하다.
- **상대 길이 단위(rem)**
  - rem(루트 이엠, 알이엠)은 합성을 회피하기 위해 만들어진 단위이다.
- **상대 길이 단위 (%)**
  - Percent(퍼센트)는 부모 크기에 따라 상대적으로 백분율 된다
- **상대 길이 단위 (vw)**
  - Viewport Width(뷰포트 너비)는 화면의 너비에 따라 결정된다. vw는 웹 브라우저의 너비 또는 스마트 기기 가로 너비에 따라 결정된다.
    - 1vw=1%
    - 100vw=100%
- 상대 길이 단위 (vh)
  - Viewport Height(뷰포트 높이)는 화면의 높이에 따라 결정된다. vh는 웹 브라우저의 높이 또는 스마트 기기 세로 높이에 따라 결정된다.
    - 1vh = 1%
    - 100vh=100%
- 상대 길이 단위 (vmin)
  - 화면에서 가장 작은 크기에 따라 결정된다. vmin은 웹 브라우저의 높이 또는 스마트 기기의 화면 중에서 가장 작은 크기에 따라 결정된다.
    - 웹 브라우저가 가로 1000px, 세로 100px일 경우:
    - 1vmin = 10px(100px의 1%)
    - 100vmin = 100px(100px의 100%)
- 상대 길이 단위 (vmax)
  - 화면에서 가장 큰 크기에 따라 결정된다. vmax는 웹 브라우저의 높이 또는 스마트 기기의 화면 중에서 가장 큰 크기에 따라 결정된다.
    - 웹 브라우저가 가로 1000px, 세로 100px일 경우
    - 1vmax=100px(1000px의 1%)
    - 100vmax=1000px(1000px의 100%)

### 꾸미기

- 글꼴 꾸미기
  - **font-size** : 글자 크기
  - **font-family** : 글씨체
    - 여러개의 글씨체를 동시에 지정할 수 있다. 이 경우 앞서 지정한 순서대로 글꼴이 적용된다. 앞의 폰트가 지원하지 않는 문자가 나타나면 그 뒤 폰트가 적용된다.
    - 마지막에 sans-serif 또는 serif를 작성하여 모든 OS에 공통 사용되는 세리프체를 추가해 글꼴이 없는 경우를 대비한다.
    - 사용하고자 하는 글꼴 이름에 공백이 들어갈 수 있기 때문에 쌍따옴표 또는 홑따옴표로 감싸준다.
  - **font-weight** : 글자 두께
    - 숫자 또는 문자로 정의 가능
    - 두께는 글꼴의 생성 과정에 따라 다양하게 처리 가능하기 때문에 사용하고자 하는 글꼴이 어떤 두께를 지원하는지 알아두는게 좋다
    - 일반적으로
      - 숫자 표기는 백단위로 100~900 까지 가능
      - 문자 표기는 normal, bold
      - 부모 요소의 상대적 크기는 (부모보다 얇게: lighter, 부모보다 굵게:bolder)
  - **color** : 글자 색상
    - CSS 에서 사용하는 색상 정의에 따른다
      - 키워드: red, blue
      - RGB(함수형): rgb(255,0,0)…
      - RGB(16진수): #ff0000
        - HEX(헥스) 코드라고도 한다.
    - 키워드 transparent를 쓰면 투명이 된다.
  - **text-align** : 글자의 가로 정렬. left, center, right값을 사용해 글자의 가로 정렬을 제어할 수 있다.
  - **line-height** : 글자의 줄간격.
    - normal 키워드를 기본으로 가지며 브라우저와 글꼴에 따라 다르지만 보통 1.2 정도의 값을 가진다.
    - CSS 단위를 사용해 값을 입력할 수 있다.
    - 단위 없이 숫자로만 입력할 수 있다.
      - 숫자로만 입력시 퍼센트 단위와 비슷하게 동작한다.
  - **letter-spacing** : 자간
    - normal 키워드를 기본으로 가진다.
    - CSS 단위를 사용해 값을 입력할 수 있다.
    - 보통 em 단위를 사용해 부모 폰트 크기에 따라 같이 조절되게 한다.
- 배경 꾸미기
  - **background-color** : 배경색
    - 글꼴 꾸미기의 color와 동일하게 CSS color 값을 사용할 수 있다.
    - currentColor 값을 사용하면 부모 요소의 글꼴 color를 상속받는다.
  - **background-image** : 배경 이미지
    - url( ‘이미지 경로’ ); 를 사용해 원하는 이미지를 배경으로 넣을 수 있다 (따옴표로 이미지 경로를 잘 감싸줘야 한다)
  - **background-repeat** : 배경 이미지의 반복
    - 배경이미지는 추가 시 이미지의 크기에 따라 바둑판식으로 계속 반복된다.
    - 지정가능한 값
      - repeat : 반복(기본값)
      - repeat-x/repeat-y: x축/y축 반복
      - round: 반복되는 이미지가 잘리지 않게 늘려서/줄여서 반복
      - space: 이미지가 잘리지 않게 고르게 분배
      - no-repeat: 반복 하지 않음
  - **background-size** : 배경 이미지의 크기
    - 단일값 입력시 배경이미지의 너비가 조절된다.
    - 두개값 입력시 너비, 높이의 제어가 가능하다.
    - contain 키워드를 사용하면 이미지가 부모크기에 맞게 비율에 맞춰 알아서 맞춰진다.
    - cover 키워드를 사용하면 이미지의 제일 작은 크기가 부모의 크기의 비율에 맞게 맞춰지며 나머지 커진 영역은 잘라낸다.
  - **background-position** : 배경 이미지의 위치
    - 키워드로 제어: top, right, bottom, left, center
    - css단위로 제어: 10px 20px(x축 y축)
    - 키워드로 제어할 때 offset을 지정할 수 있다 : right 10px center
  - **background** : 배경 이미지 속성을 한번에 작성할 수 있는 단축 속성
    - 공백으로 구분하여 배경 조건을 한번에 작성할 수 있음
    - 작성 순서는 상관없으나 위치/크기는 규칙에 맞게 함께 작성되어야 한다.

## [Feelings+Finding]

- CSS 를 작성할 때 단순히 작성 순위에 따라 우선 순위가 정해지는 거 인줄 알았는데 결합, 선택자에 따라서도 우선 순위가 있다는걸 새롭게 알게 되었다.
- 코드를 작성하면서 단위를 선택할때 픽셀 단위로만 많이 사용하였었는데 다른 상대 길이 단위들도 목적에 잘 맞춰서 사용해야겠다는 생각이 들었다.

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
