---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/10)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 10일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til12

toc: true
toc_sticky: true

date: 2024-1-10
last_modified_at: 2024-1-10
---

## [Facts]

- 가계부 구현하기, 자바스크립트 기초 사전 준비하기

## [TIL]

### 가계부 구현하기

- Use Case
  1. 현재 자산을 입력할 수 있다.
  2. 가계부 내역을 입력할 수 있다.
  3. 가계부 목록을 볼 수 있다.

### **CurrentAsset**

```jsx
export function renderCurrentAsset() {
  // 숫자에 콤마 작성 - number.toLocaleString() -> 지역에 맞게 문자열 대응
  // currentFunds가 없는 경우 - if문 사용하거나, 삼항 연산자 사용, 옵셔널 체이닝
  $currentAssetValue.textContent = store.currentFunds?.toLocaleString ?? "-";
  $currentAssetInput.value = store.currentFunds;
}
```

### Validation

```jsx
export function validatePrice(currentFunds, currentAmount) {
  // 금액이 현재 자산보다 이하인지
  return currentFunds >= currentAmount;
}

export function validateRequired({ category, description, price }) {
  // 값이 존재하는지
  return(
  Boolean(category) && Boolean(description) && Boolean(price) && price > 0;)
}
```

### **addNewHistory**

```jsx
export function addNewHistory(newHistory) {
  try {
    // store의 detailList 새로 갱신, store.currentFunds 새로 갱신
    console.log("newhistory");

    //todayId가 존재하는지 확인
    if (store.detailList[todayId]) {
      //새로운 값으로 기존 값에 재할당
      store.detailList[todayId] = store.detailList[todayId].push(newHistory);
    } else {
      store.detailList[todayId] = [newHistory];
    }

    // 현재 자산 amount를 재할당
    store.currentFunds -= newHistory.amount;
    console.log("store", store);

    updateStorage();
    return true;
  } catch (error) {
    alert(error);
    return false;
  }
}
```

### **데이터 매핑**

innerHTML을 통해서, 데이터매칭하고 가지고 있는 dateList를 반복문을 돌면서 처리

### **Formatting**

- _항목의 시간 포맷 변경: `HH:mm`_
  ```jsx
  const time = new Date(createAt).toLocaleTimeString("ko-kr", {
    timeStyle: "short",
    hourCycle: "h24",
  });
  ```
- _금액 콤마 포맷 맞추기_
  ```jsx
  ${amount.toLocaleString()}
  ${fundAtTheTime.toLocaleString()}
  ```

### **오름차순 정렬**

- sorting을 다시하고, map을 돌려야함
  ```jsx
  ${detail.sort((a,b) => b.id - a.id)}
  ```

### **removeHistory**

```jsx
export function removeHistory(dateId, itemId) {
  try {
    store.detailList[dateId] = store.detailList[dateId].filter(
      ({ id, amount }) => {
        if (id === Number(itemId)) {
          store.currentFunds += amount;
        }
        return id !== Number(itemId);
      }
    );

    updateStorage();
    return true;
  } catch (error) {
    console.log(error);
    return false;
  }
}
```

### 요구사항 분석 - 가계부 서비스 spec과 user story

- 가계부 서비스 spec
  - 소비 내역을 관리하여 나의 자산현황을 파악하고 이전 기록을 확인 하는 목적
  - Entity와 속성
    - entity: 식별할 수 있는 대상으로 정리한것
  - 자산: id, 금액, 최초 생성일자, 수정일자
  - 소비내역: id, 금액, 카테고리, 내용, 시점금액, 생성일자
- User story: 유저의 목표달성을 위한 인터렉션을 하나의 문장으로 정리한것
  - 현재 자산을 관리 할 수 있다
    - 현재 자산을 조회할 수 있다
    - 현재 자산을 등록할 수 있다
  - 소비 내역을 관리 할 수 잇다
    - 소비내역을 등록할 수 있다
    - 소비내역을 수정할 수 있다
    - 소비내역을 삭제할 수 있다

### 요구사항 분석 - user flow와 상세 flow

- user flow: user story를 기준으로, 구현 시나리오를 정리한것
  - 원칙 : 유저의 행동을 시작으로 시나리오가 시작, 유저의 행동에 따른 피드백을 제공해야함
  - 시나리오 성공 case를 먼저 작성
  - 시나리오가 실패되는 case를 나열
    - == 엣지 케이스
    - 시나리오의 조건들을 나열하고, 조건별로 실패가능한 케이스를 정리
- 가계부 서비스 - 상세 flow
  - 소비내역을 관리할 수 있다 > 소비내역을 등록할 수 있다
  - 필수조건: 자산 존재여부, 자산 금액
  - 성공시나리오: 유저는 자산이 소비할(한) 내역 이상 있는 경우 소비내역을 등록 할 수 있다
  - 실패시나리오: 유저는 자산이 소비할(한) 내역 미만이면 소비내역을 등록 할 수 없다
  1. 자산을 조회
  2. 자산이 0원이상이면 , 소비 내역을 등록할 수 있는 입력 폼을 볼 수 있음 / 자산이 0원미만이면, 소비 내역을 등록할 수 있는 입력 폼을 볼 수 없음
  3. 소비내역 등록시, 자산보다 같거나 적은 금액을 등록할 수 있음
- user story에서 의사코드(pseudocode)까지
  - User Story
  - User flow
    - 상세정리
    - diagram 시각화
    - 의사코드 정리 (구현 계획)

## [Feelings+Finding]

- 자바스크립트 이론 강의 이후 처음으로 실습하면서 가계부의 다양한 기능들을 구현해 보았는데 어렵게 느껴졌다. 단순히 이론만 공부하는것이 아니라 이렇게 실습을 통해서 개발 역량을 높이기 위해 노력해야겠다!

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
