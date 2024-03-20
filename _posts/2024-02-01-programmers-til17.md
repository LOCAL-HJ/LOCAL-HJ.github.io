---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(2/1)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 2월 1일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til17

toc: true
toc_sticky: true

date: 2024-2-1
last_modified_at: 2024-2-1
---

## [Facts]

- node js 기초에 대해서 공부

## [TIL]

### React 소개

- React는 자바스크립트의 UI 라이브러리
- React의 파생 기술인 React Native를 이용하여 데스크탑, Android, IOS에서 동작하는 어플리케이션을 개발할 수 있음

### Node.js 기초

- 자바스크립트 코드는 브라우저 내장 자바스크립트 엔진을 이용하여 실행
- 자바스크립트는 웹 브라우저에서만 사용될 수 있었음
- Node.js
  - 자바스크립트를 브라우저가 아닌 곳에서도 실행시켜보자!
  - 자바스크립트의 실행환경
  - Javascript’s Runtime
  - Javascript로 Web server 개발 가능
- web server는 url이라는 주소로 요청을 받아서, 요청 받은 주소(Url)에 알맞는 web 파일들을 브라우저에게 던져준다.
- React는 복잡한 js 파일을 쉽게 만들어내는 기술이다.
- React에서 만들어 낸 Js 파일들은 프로그램처럼 돌아간다. 그렇기 때문에, 웹 어플리케이션이라고 부른다
- React는 Node.js 없이 사용할 수 없다

---

- `node -v :` 노드 버전 확인
- `npm -v` : 버전 확인mpn
- `command + j`>> vscode 에서 panel 보이게 함

---

- **Graphic User Interface(GUI):** 아이콘 같은 그래픽을 기반으로 마우스 클릭 만으로 명령을 내릴 수 있게 하는 방식
- **Command Line Interface(CLI):** 수행할 명령을 직접 텍스트로 타이핑 해서 명령을 내리는 것

```jsx
// index.js
const calc = require("./calc");

console.log(calc);
// require 내장함수와 module.exports 내장함수는
// node js에 있는 내장함수이기 때문에 바닐라 Js에서는 이용이 제한됨
console.log(calc.sub(10, 3));
// node.js에서 기본적으로 제공하는 common JS 시스템
```

```jsx
// calc.js
//계산 기능을 하는 파일

const add = (a, b) => a + b;
const sub = (a, b) => a - b;

module.exports = {
  moduleName: "calc module",
  add: add,
  sub: sub,
};
// 모듈을 내보냄
// 객체 단위로 모듈을 내보낼 수 있음
```

---

- **NPM (Node Package Manager)**: Node.js 패키지 관리 도구 / **패키지**: Node.js 모듈
- **`npm init`** 명령어
  - Node.js 프로젝트를 시작할 때 사용됨
  - 새로운 **`package.json`** 파일을 생성하는 과정을 안내
- **`package.json`** 파일 (환경 설정 파일)

  - 프로젝트의 메타데이터와 의존성(dependencies), 스크립트(scripts) 등을 정의
  - 나중에 프로젝트에 라이브러리나 프레임워크를 추가할 때 (**`npm install <패키지명>`** 명령어 사용) 그 의존성을 관리하는 데 사용됨
  - 프로젝트를 다른 개발자와 공유할 때 중요한 정보를 제공하며, 다른 환경에서 프로젝트를 재구성하는 데 필요한 모든 정보를 포함
  - **main** : 패키지를 실행할때 어떤 파일을 실행해야 되는지를 명시
  - **scripts** : 패키지를 개발하면서 자주 실행해야하는 명령어 같은 것들을 사전에 정의해둘 수 있는 곳

    ```jsx
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "node index.js"
    }, // start만 입력을 해도 node index.js 가 실행이 됨

    ```

---

- 다른 사람들이 만든 모듈을 사용하기 위해서 [https://www.npmjs.com/](https://www.npmjs.com/)로 이동
- [https://www.npmjs.com/](https://www.npmjs.com/) : nodejs 패키지들 많이 업로드 되어 있음
- npm 사이트에 들어가서, 기능에 따라서 검색해서 패키지를 다운로드해서 사용하면 됨.

  <img width="388" alt="2" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/9a69f810-16b8-4d6c-86d0-8397c12251d9">

- 위와 같은 명령어를 입력하면 된다

```jsx
"dependencies": {
    "randomcolor": "^0.6.2"
} // 패키지가 추가 되어 있음, 패키지 버전 기록
// ^0.6.2 => 0.6.2버전 이상으로 설치했다 라는 뜻.
```

<img width="144" alt="3" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/d89cf1de-b01d-4f7a-b949-6034d8fef557">

: 외부 패키지 보관소

```jsx
// randomColor 실행
const randomColor = require("randomcolor");
console.log(randomColor());
```

- package-lock : 설치한 패키지들이 정확히 어떤 버전으로 설치되어있는 지 확인할 수 있음.

## [Feelings+Finding]

- 예전에 node js를 공부했었는데 이번에 강의를 들으면서 까먹었던 부분들을 다시 공부할 수 있었고 더 정확히 개념을 잡을 수 있는 계기가 되었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
