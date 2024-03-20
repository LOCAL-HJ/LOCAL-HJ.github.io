---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/31)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 31일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til16

toc: true
toc_sticky: true

date: 2024-1-31
last_modified_at: 2024-1-31
---

## [Facts]

- 프로토타입 제작

## [TIL]

### 준비

- 피그마 로컬 폰트 사용 설정
  - 피그마를 브라우저에서 사용하는 경우 font installers를 다운받아야만 컴퓨터에 저장된 로컬폰트를 사용할 수 있다
  - 피그마 데스트톱 앱을 사용하는 경우는 font installers를 필요로 하지 않음
- ios & Material Design guideline
  - 애플의 Human Interface Guidelines: [https://developer.apple.com/design/human-interface-guidelines](https://developer.apple.com/design/human-interface-guidelines)
  - ios 17 디자인 리소스: [https://www.figma.com/community/file/1248375255495415511](https://www.figma.com/community/file/1248375255495415511)
  - 구글의 Material Design 3: [https://m3.material.io/components](https://m3.material.io/components)
  - Material 3 디자인 리소스: [https://www.figma.com/community/file/1035203688168086460](https://www.figma.com/community/file/1035203688168086460)
- 레퍼런스 찾기
  - 핀터레스트: https://www.pinterest.co.kr/
  - WWIT: [https://wwit.design/](https://wwit.design/)
- Unsplash
  - 언스플래시: 무료 이미지 및 사진: [https://unsplash.com/ko](https://unsplash.com/ko)
  - 언스플래시 플러그인: [https://www.figma.com/community/plugin/738454987945972471](https://www.figma.com/community/plugin/738454987945972471)
    - 피그마 상단 tool 바 plugins 에서 unsplash 검색해서 사용할 수 있음
- Color, Font, Icon
  - 컬러 제너레이터: [https://mycolor.space/?hex=#4A51E9&sub=1](https://mycolor.space/?hex=#4A51E9&sub=1)
  - 눈누: 상업적 이용 가능한 무료 폰트: [https://noonnu.cc/](https://noonnu.cc/)
  - 추천 폰트: [https://cactus.tistory.com/306](https://cactus.tistory.com/306)
  - 추천 아이콘: [https://www.figma.com/community/file/1014241558898418245](https://www.figma.com/community/file/1014241558898418245)

### 앱 제작

- prototype
  - position: scroll with parent
- top, bottom bar 부터 제작
- touch area를 포함해야함 >> 오토레이아웃 설정
- 4, 8의 배수
- 모바일 14px이상
- `command + r` : 한번에 rename
- command 누르고 여러개 누르면 다중 선택 가능
- 프레임 만들때 shift 누르면 정사각 형태로 만들 수 있음
- 결과

  <img width="222" alt="1" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/a953df60-50f6-4795-9921-577fbede4762">

### 데브모드

- section에 Ready for dev 설정 가능
- 디자인 모드와 달리 데브모드에서는 레이어 중첩구조를 선택할때 가장 아래에 있는 레이어가 선택됨

## [Feelings+Finding]

- 실습을 통해 배운 내용을 적용하여 피그마 사용법을 익힐 수 있었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
