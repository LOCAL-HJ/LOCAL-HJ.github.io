---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/3)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 3일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til7

toc: true
toc_sticky: true

date: 2024-1-3
last_modified_at: 2024-1-3
---

## [Facts]

- Bonus 강의 수강, 실습

## [TIL]

- mailto: 이메일 주소 → 메일 폼 생성해주는 링크

```html
<a href="mailto:rlaguswl221@naver.com"></a>
```

- 블록레벨요소는 크기를 지정해주고 margin값 좌우를 auto로 주면 중앙으로 온다

```css
.box {
  grid-template-columns: 200px 1fr;
}
/* 2개의 컬럼을 지정해주고 첫번째 컬럼은 200px, 나머지 컬럼은 200px을 제외한 나머지 부분으로 auto와 같은 처리를 한다 */
```

- font 먼저 불러오고 css 파일을 불러오는 것이 좋다: css파일을 먼저 불러오게 되면 기본 브라우저 폰트가 보이다가 중간에 설정한 폰트로 바뀔수도 있기 때문이다

```html
<!-- fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap"
  rel="stylesheet"
/>
<!-- core -->
<link rel="stylesheet" href="style.css" />
```

- **`z-index`**는 CSS 속성 중 하나로, 요소의 쌓임 순서를 결정하는 데 사용된다. HTML 문서에서 여러 요소가 겹쳐져 있을 때, **`z-index`**를 이용하여 어떤 요소가 다른 요소 위에 나타날지 결정할 수 있다
  - 기본적으로, HTML 요소들은 문서 흐름에 따라 쌓이게 되는데, **`z-index`**를 사용하면 이 쌓임 순서를 변경할 수 있다. **`z-index`** 속성은 정수값을 가지며, 값이 클수록 화면 상단에 위치하게 된다.
- a태그는 inline 레벨 요소이지만 block 레벨 요소를 가질 수 있다

```css
/* #main ul{
  margin-top:16px;
}
#main ul:first-child{
  margin-top:0;
} */

#main li:not(:first-child) {
  margin-top: 16px;
}

/* 위(주석처리된 것)처럼 작성할 수 도 있고 아래처럼 작성할 수도 있음 */
```

```css
#main li a {
  display: flex;
  gap: 16px;
  align-items: center;
  height: 50px;
  box-shadow: 0px 2px 8px #ecf0f1;
  border-radius: 4px;
  overflow: hidden;
}
/* overflow : hidden; 으로 초과된걸 잘라버리면서 border-radius를 살릴수 있음 */
```

- justify-content는 축을 바꾸는 것이니까 글자까지 가운데 정렬 시키려면 text-align: center로 해야한다

## [Feelings+Finding]

- clone coding을 하면서 배웠던 것들을 활용해볼수 있었다 ☺️

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
