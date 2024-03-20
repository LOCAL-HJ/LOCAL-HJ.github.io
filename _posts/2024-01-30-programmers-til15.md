---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/30)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 30일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til15

toc: true
toc_sticky: true

date: 2024-1-30
last_modified_at: 2024-1-30
---

## [Facts]

- 오토레이아웃
- 컴포넌트
- 반응형 설정

## [TIL]

### 오토레이아웃 - 기본

- 오토레이아웃으로 만들고 싶은 레이어들을 선택하고 단축키 `shift + a`
- 오토레이아웃 설정하면 자동으로 정렬이 됨
- 오토레이아웃을 제거를 하고 싶으면 단축키 `option + shift + a`
- `command + shift + g` : 개별 레이어 상태로(싱글 레이어)

### 오토레이아웃 - 리사이징 이론, 실습

- Horizontal resizing, Vertical resizing
  - fixed width(부모의 오토레이아웃 영역은 고정), Hug contents(자식 요소의 크기에 따라서 자동으로 resizing 된다)
  - fixed height, Hug contents
- 오토레이아웃 하위에 있는 레이어도 동일하게 resizing property 가 생김
  - fixed width, fill container(하위 레이어가 채운다)
  - fixed height, fill container
- 실습
  - 단순히 싱글레이어에 영역을 지정하기 위해 오토레이아웃을 사용할 수 도 있음
  - 오토레이아웃을 설정하면 자동으로 마진값과 패딩값이 설정됨
    - 마진값 auto인 경우: 균등값으로 나눠서
    - 음수값 줄 수 있음
  - `shift`를 누르고 이동하면 동일한 좌표에서 움직이게 된다

### 오토레이아웃 - 패널 살펴보기, 추가 장점

- 오토레이아웃이 전개되는 방향
  - vertical layout: 부모 넓이를 넘어가도 보임
  - Horizontal layout: 부모 넓이를 넘어가도 보임
  - wrap : 부모의 오토레이아웃의 정해진 가로 넓이를 넘어가는 경우 자동으로 줄바꿈해줌
- 각각의 패딩값을 설정해줄수도 있음
- Canvas stacking : 겹쳐지는 레이어의 순서를 설정
  - first on top
  - last on top

### 오토레이아웃 - 실습

- 오토레이아웃을 설정하면 콘텐츠 내용이 바뀌어도 레이어 형태를 유지할 수 있음
- stroke 가 적용이 안되는 이유: 부모에 무언가 적용을 하는 경우 레이어에 clip content를 적용시켜야 정상적으로 작동함
- `command + d` : 행동 복제
- return 버튼을 누르면 하위에 있는 레이어들 한번에 클릭

### 컴포넌트 - 기본, 베리언트(Variant)

- 컴포넌트란 언제든지 재사용할 수 있게 정의한 디자인 요소 (버튼이나 아이콘 때로는 레이아웃 등)
- 레이어 선택 후 create component 또는 `option + command + k`
- assets에서 컴포넌트 리스트 확인할 수 있음
- 메인컴포넌트(최초로 만든것)와 인스턴스
  - 메인컴포넌트에 업데이트가 있으면 인스턴스도 변경사항이 반영이 됨
- 더보기 에서 Detach instance 를 하게 되면 더이상 레이어는 독립된 레이어로 변경됨
- 메인 컴포넌트가 다른 페이지에 있다고 하더라도 인스턴스 사용 가능

---

- properties 는 메인 컴포넌트에만 적용할 수 있는 패널
  - variant
- Current variant
- variant는 독립된 네임을 가져야함

### 컴포넌트 - 실습

- variant 값을 true / false, on / off 설정하면 토글로 나타남

### 반응형 설정 - Constraints

- Constraints는 css의 position과 유사함 (부모를 relative로 보고 자식요소를 absolute로 봄)
- Left and right, Top and bottom: 부모 프레임의 사이즈가 조정될때 그에 맞게 여백을 두고 사이즈 조정이 된다(채운다)
- `command` 누른채 사이즈 조정하면 하위에 있는 레이어와 상관없이 프레임 사이즈가 변경이 된다

### 반응형 설정 - min width, max width

- 오토레이아웃을 설정한 경우에 min width, max width을 설정해줄 수 있음

## [Feelings+Finding]

- 피그마에서 오토레이아웃, 컴포넌트, 반응형 설정에 대한 실습을 통해 학습한 내용을 CSS 지식과 연계하여 적용하는 방법을 이해할 수 있었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
