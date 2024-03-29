---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/29)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 29일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til14

toc: true
toc_sticky: true

date: 2024-1-29
last_modified_at: 2024-1-29
---

## [Facts]

- 피그마 소개
- 디자인 기초: 컬러, 폰트
- 피그마 툴

## [TIL]

### 피그마 소개

- 벡터기반의 UI 디자인 툴 > 확대를 하거나 축소를 해도 깨지지 않음 - SVG
- 비트맵 (픽셀) - PNG 등

### 디자인 기초: 컬러, 폰트

- Munsell 20색상환
- 대비 >> 디자인의 의도를 명확히 전달할 수도있음
  - 보색 대비: 색상환에서 마주보고 있는 정반대의 위치 색상을 사용하는 것
    - ex. 초록색과 빨간색, 보라색과 연두색
    - 강한 인상을 준다
  - 유사 대비: 색상환에서 인접한 3가지 색상을 사용하는 것
    - 조화롭고 차분한 느낌
- 60-30-10 ratio
  - Main color : 60%
  - Secondary color : 30%
  - **Accent color : 10% (10%미만)**
- 계층 구조 표현
  - 색채를 활용해서 표현할 수 있음
  - 타이포그래피(폰트의 크기나 굵기) - 요소간의 중요도나 위계를 분명하게 표현할 수 있음
- 접근성
  - 저시력자 등 콘텐츠를 명확히 인식할 수 있게끔 해야함
- 세리프
  - 서체의 종류
  - 삐침이 있다
  - 가독성이 좋다
- 산세리프
  - 모서리에 삐침이 없다
  - 현대적이고 도시적인 느낌

### 피그마 툴 학습하기 - 인터페이스

- 각 페이지는 고유의 캔버스를 가지고 있음

### 피그마 단축키

- 피그마내에서 단축키를 확인하려면 `Control + Shift + ?`

### 피그마 툴 학습하기 - 프레임(Frame), 섹션(Section)

- **프레임: 바탕이 되는 도화지를 만드는 방법**
  - 단축키 F
  - 레이어를 `command + G`를 통해서 단순히 grouping 할 수도 있지만 프레임으로 그룹화할 수도있음
- **섹션: grouping을 할 수 있는 방법 중 하나**
  - `shift + s`
  - **프레임, 그룹 보다 상위 개념**
  - 섹션을 프레임으로 묶을 수 없음
  - 섹션안에 프레임은 넣을 수 있음
  - 워크스페이스를 정돈하는 역할로 사용 (ex. 미완성본과 작업중)

### 피그마 툴 학습하기 - 기본 도형, 텍스트(Text)

- **도형**
  - shift 를 누른 상태로 생성하면 비율에 맞춰서 만들 수 있다
  - 우측 패널을 이용해서 꼭짓점 갯수 변경 가능
- **텍스트**
  - auto width
  - auto height
  - 클릭하고 드래그 - fixed size

### 피그마 툴 학습하기 - 코멘트(Comment), 좌측 사이드바

- **코멘트**
  - / : 팝업 코멘트 (시간 지나면 사라짐)
- **좌측 사이드바**
  - 숨김 버튼: 레이어가 캔버스에서 보이지 않음
  - 잠금 버튼: 캔버스에서 선택이 되지 않음, 레이어 패널에서는 선택이 가능
  - 숨김버튼, 잠금버튼 드래그 하면 한번에 설정 가능

### 피그마 툴 학습하기 - 정렬(Align), 프레임 사이즈와 오리엔테이션(Frame & Orientation)

- **정렬**
  - 우측 사이드바
  - 두가지이상의 레이어를 선택한 경우 정렬기능 활성화
  - 프레임 안에 레이어를 정렬할때도 사용
- **프레임 사이즈**
  - Frame 옆 화살표 버튼
- **오리엔테이션**
  - Portrait: 세로형
  - Landscape: 가로형
  - Resize to fit: 프레임 안에 레이어가 있을때 내부에 있는 레이어의 크기만큼 프레임이 resize

### 피그마 툴 학습하기 - 포지션(Position), 디멘션(Dimension)

- 프레임 안에 레이어가 존재하는 경우는 x,y 좌표가 부모인 프레임 기준으로 함
- 디멘션: 가로값과 세로값이 따로 동작, 하지만 링크 모양을 통해 연결시켜주면 비율에 맞게 변경이 됨
- Rotation
- Corner radius : 모서리를 둥글게 할 수 있음
- 입력값에 사칙연산 사용 가능
- clip content : clip content 를 체크- 프레임 영역 만큼만 보여주겠다

### 피그마 툴 학습하기 - 레이어(Layer), 텍스트(Text)

- 레이어 투명도 조절 가능
  - 블렌드 모드
- Line height : 숫자를 적기보다는 비율로 많이 작성(ex. 130%)
- Letter spacing: 자간 설정, 음수 작성 가능, 퍼센트. 픽셀 둘다 사용 가능
- paragraph spacing: 문단 사이 간격 설정
- ul,ol 자동으로 설정됨
- Truncate text : 말줄임 기능이 있음

### 피그마 툴 학습하기 - 채우기(Fill), 선(Stroke)

- **Fill**
  - solid
  - gradient
  - image
    - fill
    - fit
    - crop
    - tile
- **Stroke**
  - Center, inside, outside
  - svg인 경우 center 만 지원

### 피그마 툴 학습하기 - 선택된 컬러 (Selection colors), 이펙트(Effects), 내보내기(Export)

- **Selection colors**
  - 복수의 레이어를 클릭을 하면 레이어에 사용된 컬러를 확인할 수 있음
  - 컬러를 한번에 변경 가능하다
- **Effects**
  - 그림자 기능, 흐림 효과
  - background blur을 사용할때 주의해야 할 점은 fill layer을 반드시 추가해야 함, 투명도를 설정해야 함
- **Export**
  - 다운받거나 추출 가능
  - scale 설정 가능
  - 파일 형식 설정 가능
  - 여러개의 레이어를 한번에 다운 받을 수 있음

## [Feelings+Finding]

- 피그마의 기초적인 부분을 처음 배워보았는데 재미있었다. 😄 다음 강의들을 들으면서 많은 기능들을 배워보고 싶다는 생각이 들었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
