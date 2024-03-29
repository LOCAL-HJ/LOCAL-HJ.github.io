---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/4)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 4일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til8

toc: true
toc_sticky: true

date: 2024-1-4
last_modified_at: 2024-1-4
---

## [Facts]

- 실습환경 셋팅, javascript 언어의 특징과 표준화에 대해서 공부

## [TIL]

### 실습환경 셋팅하기

- IDE: 문서 작성 및 편집, 문서실행 등 - vscode,,
- Terminal
- Browser

### 브라우저와 디버깅

- 디버깅 방법
  - 코드내에 log함수 심기
    - console.log : 입력한 값을 콘솔에 한줄 씩 출력해준다.
    ```jsx
    console.log("temp: ", temp);
    ```
    - 이를 위한 vscode snipper을 미리 셋팅하여 활용하는 방법도 있음
    - console.dir : 주입된 값의 모든 속성을 확인할 때 사용
    ```jsx
    function student(name, age) {
      //
    }
    console.dir(new student("hyunji", 24));
    ```
    - console.table : 표 형식의 데이터를 테이블로 표현한다, 색인과 값을 테이블 형태로 표현하기 때문에 , 컬렉션 데이터를 확인하는 용도로 적합하다
  - 개발자 도구 > Source 탭 활용

### JavaScript 언어의 특징

- 컴퓨터가 작성된 코드를 이해하는 방법: 사람이 이해한 언어로 작성되면 기계어로 번역이 되어야 한다
  1. 컴파일러 언어 : 사람이 코드를 작성, 기계어로 변환, 기계에서 실행
  2. 인터프리터 언어 : 사람이 코드를 작성, 기계에서 실행, 변환하며 진행

1. **자바스크립트는 인터프리터 언어이다**
   - 컴파일 단계가 없음
   - 컴파일 언어에 비해, 실행 속도가 느림 > 모던 브라우저내의 V8엔진에서는 속도 개선이 됨
2. 동적 타입 언어
   - 동적 타입 언어 : 변수에 들어가는 값에 따라서, 런타임에 타입이 추론된다
3. 함수는 일급 객체
   - 함수는 일급객체의 특징을 가진다.
   - 함수는 객체와 동일하게 사용할 수 있다
   - 함수는 값과 동일하게 취급한다
     - 변수할당문, 객체 프로퍼티값, 배열의 요소, 함수 호출의 인수, 함수 반환문
4. 프로토타입 기반의 상속
   - 언어가 갖고 있는 프로토 타입 체이닝 구조를 통하여 상속가능
5. 여러 프로그래밍 패러다임 지원
   - 명령형 프로그래밍, 함수형 프로그래밍, 객체지향 프로그래밍

### JavaScript 표준화

- 자바스크립트의 발전
  - 자바스크립트도 탄생 이후로 성장 시점마다 버전이 존재
  - 자바스크립트를 사용하는 개발자는 버전을 확인하며 개발
    - ECMAScript 2015
    - …
    - ECMAScript 2022
- ECMAScript2015 = ES2015 = ES6
  - 목표: 대규모 어플리케이션, 라이브러리 생성, 다른 언어의 컴파일
  - 개선사항 : 모듈, 클래스 선언, 블록레벨 스코프, iterator와 generator, 비동기 프로그래밍, promise, 구조분해 패턴 등의 개선이 존재
- ECMAScript와 브라우저
  - 브라우저는 브라우저의 버전마다, 지원하는 자바스크립트 스펙이 상이 > ECMAScript의 기준을 따라가지는 않는다.
  - 개별 기능의 지원: Caniuse 확인 가능
- 개발에 사용하고 싶은데 브라우저 지원이 안될 경우
  - polyfill과 babel을 사용한다
  - polyfill: 지원하지 않는 브라우저에서 최신기능을 제공하기 위해 필요한 코드, 폴리필은 브라우저가 다른 방식으로 동일한 기능을 구현 하는 문제를 해결하는데 사용
  - Babel: 이전 버전의 브라우저에서 ES6 이전 버전의 Javascript로 변환하는데 사용되는 도구, 문법을 번역 및 변환, 폴리필 기능

## [Feelings+Finding]

- 디버깅 방법과 자바스크립트 언어의 특징, 표준화 등과 같이 기본 개념에 대해서 공부할 수 있는 시간이었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
