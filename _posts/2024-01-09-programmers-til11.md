---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/9)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 9일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til11

toc: true
toc_sticky: true

date: 2024-1-9
last_modified_at: 2024-1-9
---

## [Facts]

- 자바스크립트 : 객체와 빌트인 객체 그리고 매커니즘에 대해 공부함

## [TIL]

### 객체

- 객체: 속성을 가진 독립적인 개체
  - 객체는 속성으로 구성된 집합이다
- 자바스크립트는 객체 기반의 프로그래밍 언어: 자바스크립트를 구성하는 대부분이 객체이다. (원시값 이외의 값)

```jsx
const 객체명 = {
  속성: 값,
  속성2: 값,
};
```

- 객체 Object - 속성 property

  - 속성은 키와 값 사이의 연결관계, key-value
  - 객체의 속성은 JavaScript의 변수와 유사한데, 객체에 속해있다
  - 속성 접근 방법
    - 마침표 표기법: `objectName.propertyName`
    - 대괄호 표기법: `objectName[“propertyName”]`
  - 속성에는 값 뿐만 아니라 함수도 할당 가능하다.

    - method: 객체에 속해있는 함수를 method라고 한다, 메서드는 다른 함수와 동일하게 정의하지만, 객체 속성에 할당 되어있다. ECMAScript 2015에서는 짧은 구문으로 작성가능하다

    ```jsx
    const 객체 = {
      속성: function () {
        console.log("Hi");
      },
      속성2() {
        console.log("Hello");
      },
    };

    객체.속성();
    객체.속성2();
    ```

- 객체 Object - 생성방법

  1. 리터럴 표기로 객체 생성

     ```jsx
     const animal = {
     	name:'puppy';
     }
     // 변수명 : 새로운 객체의 이름
     // 콜론 앞 속성 이름 (name) : 식별자
     // 콜론 뒤 값('puppy') : 속성에 할당할 표현식
     ```

  2. 생성자 함수로 객체 생성

     - 속성만 같고 값만 다른 객체를 여러개를 생성해야할때, 번거로움이 있다
     - **_생성자 함수를 사용하면, 템플릿처럼 사용하여 속성이 동일한 객체를 여러개 생성할 수 있다_**
       - 생성자 함수: new 키워드와 함께 객체를 생성하고 초기화하는 함수
     - 생성자 함수를 정의한후, 생성자 함수를 활용하여 객체 인스턴스를 생성한다.(인스턴스 new 키워드로 생성된 객체)
       - **생성자 함수는 대문자로 시작(일반함수와 구분)**
       - this 키워드로 속성을 정의하여, 생성될 인스턴스를 가리키게 해둔다
       - new 연산자를 활용하여 인스턴스를 생성한다

     ```jsx
     function Animal(name, age) {
       this.name = name;
       this.age = age;
     }

     new Animal("rabbit", 3);
     ```

  3. Object.create로 객체 생성

     - 생성자 함수처럼 동일한 속성값을 갖는 객체를 생성할 수 있다
     - Object.create(객체)

     ```jsx
     const Animal = {
       name: "cat",
       age: 3,
       getName: function () {
         console.log(this.name);
       },
     };

     const Puppy = Object.create(Animal);
     Puppy.name = "Puppy";
     Puppy.getName(); // 'Puppy'
     ```

- Object 객체
  - 생성자: new Object()
  - 정적 method
    - 객체 자체와 관련된 method, 객체 속성과 관련된 method, 객체 속성 값과 관련된 method
  - 인스턴스
    - Method: hasOwnProperty(), isPrototypeOf(), propertyIsEnumerable(),toLocaleString(),toString(),valueOf()
- Object 객체 - 정적 method
  - 객체 자체
    - 객체 복사 assign
    - 객체 신규 생성 create
    - 객체 고정 freeze, preventExtensions, seal
    - 객체 상태 확인 isExtensible, isFrozen, isSealed
    - 객체를 배열로 반환 entries, fromEntries
    - 객체 prototype getOwnProperyOf, setOwnPropertyOf
  - 객체 속성
    - 객체 속성 추가 defineProperty, defineProperties
    - 객체 속성 서술자 getOwnPropertyDesciptor, getOwnPropertyDescriptors
    - 객체 속성 열거 getOwnPropertyNames, keys, getOwnPropertySymbols
  - 객체 속성의 값
    - 객체 값 비교: is
    - 객체 값 열거: values

### 객체 속성 control

- 객체 속성 조작하기
  - 객체는 원시타입과 다르게 변경 가능한 값
  - 객체는 전달하는 과정에서 참조형태로 전달됨
    - 이는 객체의 변경이 일어날때 참조된 객체들도 같이 변경이 되는 문제점을 야기한다
    - 때문에 의도한 동작이 되기 위해서는 (1.객체의 속성 동적 생성 2.객체의 속성들 나열하기 3. 객체의 속성 삭제하기)와 같은 조작을 적절히 사용해야 한다
- 객체 속성 조작하기 - 동적생성 : 객체에 존재하지 않는 속성을 참조하고 할당문을 통해 값을 할당하면 속성이 동적으로 생성되고 추가된다

  ```jsx
  const person = {
    name: "hyunji",
    age: 24,
  };

  person.gender = "female";
  ```

- 객체 속성 조작하기 - 나열하기 : 객체의 속성을 나열하는 3가지 방법

  1. for…in : 모든 열거 가능한 속성을 순회한다.(객체의 프로토타입 체인의 속성까지)
  2. Object.keys(객체) : 객체 자신의 열거 가능한 속성 이름을 배열로 반환
  3. Object.getOwnPropertyNames(객체) : 객체 자신만의 모든 속성을 배열로 반환

  ```jsx
  const parent = {
    age: 55,
    gender: "female",
  };

  function Child(name) {
    this.name = name;
  }

  Child.prototype = parent;

  const child = new Child("lee");

  Object.keys(child); // ['name']
  Object.getOwnPropertyNames(child); // ['name']
  for (const key in child) {
    console.log(key);
  } // 'name' 'age' 'gender'
  ```

- 객체 속성 조작하기 - 삭제하기
  - delete 연산자로 속성 삭제
  - delete 속성 이름 : ex) `delete person.name;`
  - 반환값 : true

### 객체 비교와 복사

- 객체는 참조 타입 Reference type : 모든 연산이 참조값(메모리 주소)으로 처리
  - 객체 비교
  - 객체를 복사할 경우
- 객체 비교: 객체를 서로 비교하면 객체 속성과 값이 같은 객체여도, 참조값이 다르므로 서로 다름, 자기 자신과의 비교에서만 true
- 동일한 객체를 생성해야할 때
  - 정의된 객체를 다른 변수에 그대로 할당 할 경우, 동일한 메모리 주소만 할당됨
  - 둘 중 하나의 객체를 수정한다면, 동일한 메모리 주소이기때문에 두 변수가 참조하고 있는 객체가 수정되어 결과적으로 2가지 객체 모두 변경사항에 영향을 받는다
  - 객체 복사의 2가지 방법: 얕은 복사, 깊은 복사
- **얕은 복사**: 복사된 객체의 속성 중 하나라도 같은 참조를 하고 있게 되면 얕은 복사로 복사되었다고 한다
  - 객체의 속성 중 참조타입이 없는 경우에만 얕은 복사 방법 권장
  - 방법
    - Object.assign({}, 복사할 객체)
    - spread 연산자
      - {…복사할 객체}
- **깊은 복사**: 복사된 객체의 속성 중 하나라도 같은 참조를 하고 있는 속성이 없다면 깊은 복사로 복사되었다고 한다
  - 방법
    - 재귀함수를 이용한 복사 (라이브러리: lodash - cloneDeep)
    - JSON.stringify : 객체 → 문자열로 변환(참조가 끊어짐) → 객체로 변환

### 객체의 종류

- 표준 빌트인 객체 ECMAScript
  - 기초 객체 : Object, Function, Boolean, Symbol
    - 오류 객체: Error
    - 숫자 및 날짜: Number, BigInt, Math, Date
    - 텍스트 처리: Regex(정규 표현식), String(문자열)
    - Collection
      - Index based collection: Array(배열)
      - Key based collection: Map, Set, …
  - 구조화 된 데이터: JSON
  - 제어 추상화 객체 (Promise, Generator, AsyncFunction, …)
  ***
  - 빌트인 객체 형태
  - 정적 static: 속성, method (정적이란 객체를 인스턴스화 하지 않고 바로 참조할 수 있는 속성과 메서드를 말한다)
  - 인스턴스 instace: 속성, method
    - \{{객체.prototype.인스턴스method}}
      - e.g Number.prototype.toFixed()
    - 기본적으로 Object 객체의 속성을 상속받음: 프로토타입 메서드들을 모두 상속 toString(), toLocaleString(), valueOf()
    - 함수로써 바로 호출 사용
- 호스트 객체 (브라우저 기준): DOM API

### Number, Math

- Number 객체 : 숫자를 표현하고 다룰때 사용하는 원시 래퍼 Built-in 객체
  - 함수로 바로 사용가능 : Number(‘1.2’) : Number로 타입 전환
  - Static 속성과 메서드
    - 속성: MAX_VALUE, MAX_SAFE_INTEGER, NaN,…
    - 메소드: 확인하는 용도: isNaN, isFinite,isInteger,… / 파싱하는 용도: parseInt, parseFloat
  - 생성자 함수: Number.prototype / 인스턴스 메서드 : toFixed, toLocalString,…
  - 변수 또는 객체의 속성이 숫자를 갖고 있으면, **Number 객체 인스턴스 생성 없이 Number의 인스턴스 속성과 메서드 사용가능**
- Math 객체 : 수학적인 상수와 함수를 위한 속성과 메서드를 가진 Built-in 객체 (숫자 데이터 타입만 지원)
  - Math는 생성자가 아님, 정적 속성과 메서드만 지원
  - Static 속성과 메서드
    - 속성: PI, E, …
    - 메소드
      - abs(x), pow(x,y), sqrt(x),
      - ceil(x), floor(x), round(x),
      - max(x,y,…), min(x,y,…),
      - random()
      - …

### Date

- Date 객체 : 1970년 1월 1일 UTC 자정과의 시간 차이를 밀리초 단위로 나타낸것
  - UTC: 국제 표준 시간의 협정 세계시 - 그리니치 평균시(GMT)에 기반함
  - 한국은 UTC 기준으로 9시간이 더해진다
    - getTimezoneOffset() // UTC - 현지 시간대 (분단위 반환)
  - 특정 시간대(현재시간을 포함)를 가져올수도, 다시 셋팅할 수 있는 method를 제공
  - 함수로 호출 : Date() → Sat Jan 9 2024 18:43:12 GMT+0900(한국 표준시)
  - 생성자 함수 : Date.prototype
  - Static 속성과 메서드 : 속성 - 없음, 메소드 - now(), parse(), UTC()
- Date 인스턴스 메서드
  - new Date()
  - new Date(시간 문자열)
  - 시간을 get하는 메서드
    - 인스턴스 메서드 - 시간 갖고 오기
    - 기본 - 현지시간 기준
      - 연,월,일, 요일 갖고오기: getFullYear(), getMonth()-1월이 0부터 시작, getDate(), getDay()- 일요일이 0부터 시작 (toLocalDateString()활용시 : 현지에 맞는 요일 문자열 얻을 수 있다)
      - 시,분,초, 밀리초 갖고오기: getHours(), getMinutes(), getSeconds(), getMilliseconds()
    - -UTC-: UTC 기준
      - 한국 시간은 9시간 차이나므로, getHours와 getUTCHours 만 차이나고 나머지는 동일한 값을 반환
    - UTC로 부터 ~ 걸린 시간 갖고오기(밀리초기준): getTime()
    - UTC와 현지시간대 차이 갖고 오기(분 기준): getTimezoneOffset()
  - 시간을 set하는 메서드
    - 인스턴스 메서드 - 시간 set하기
    - 기본 - 현지시간 기준
      - 연, 월, 일 요일 갖고오기: setFullYear(), setMonth(), setDate(), setDay()
      - 시, 분, 초, 밀리초, 갖고오기: setHours(), setMinutes(), setSeconds(), setMilliseconds()
    - -UTC-:UTC기준
      - 한국시간은 9시간 차이나므로, setUTCHours 사용시 유의
      - UTC 로부터 ~ 걸린시간 셋팅하기 (밀리초 기준): setTIme()
  - Date 객체 - Object 메서드 오버라이딩: 최상위 객체가 갖고 있는 메서드 중 상속받는 메서드가 있다
    - valueOf(): UTC와 기준 시점 사이의 밀리 세컨즈 차이값, getTime()과 동일한 값
    - toString(): Sat Jan 9 2024 18:43:12 GMT+0900(한국 표준시) , Date()와 동일한 값

### 문자열

- 문자열 - 생성방법
  - 문자열 리터럴로 표현되며, 쌍따옴표, 따옴표를 사용하여 표현
    - ECMAScript 2015이상에서는 템플릿 리터럴(백틱`)사용 가능
  - String 객체 사용
- 문자열 특징
  - 문자열 내에 이스케이프 문자 사용가능 (\n)
  - 줄바꿈 문장 표현 가능
    - 이스케이프 문자 활용(\n)
    - 템플릿 리터럴 활용(백틱 `)
  - 데이터 보관시 문자열 형태로 저장 유용
    - 텍스트 형태로 저장
    - 객체 형태 → JSON.stringify로 변환하여 저장
- 문자열 조작
  - 문자열 요소 접근
    - charAt
    - 유사 배열이라 배열처럼 접근
  - 문자열 비교
    - 알파벳 순을 비교하여서 순서가 뒤에 올 수록 크다고 판단
  - 변수 또는 객체의 속성이 문자열을 갖고 있으면 String 객체 인스턴스 생성없이 String 의 인스턴스 속성과 메서드 사용 가능
- String 객체 : 문자열을 다룰때 사용하는 원시 래퍼 Built-in 객체
  - 함수로 바로 사용가능
    - String(…): 문자열로 타입 전환
  - 정적 메서드: fromCharCode, fromCodePoint, raw
  - 생성자 함수: String.prototype
    - 인스턴스 속성: length
    - 인스턴스 Method
      - 문자열 체크(get)
        - 접근: at(), charAt(), charCodeAt(), codePointAt()
        - 찾기: indexOf(), lastIndexof(),search()
        - 포함여부: includes(), startsWith(),ensWith(), match(정규표현식), metchAll(정규표현식)
        - 비교: localeCompare()
      - 문자열 변경(set): 추가하기, 합치기, 분리하기, 변경하기
        - toLocaleLowerCase(), toLocaleUpperCase(),toString()
        - replace(), replaceAll()
        - 추가하기 : padEnd(), padStart(), repeat()
        - 합치기: concat(), 산술연산자
        - 분리하기: slice(), substring(), split(), trim(), trimStart(), trimEnd()

### 정규 표현식

- 문자열에서 특정 문자 조합을 찾기 위한 패턴 (== 정규식)
- 패턴 작성하는 방법: 단순 패턴 사용 / 특수 문자 사용: 어서션, 문자클래스, 그룹과 범위, 수량자, 유니코드 속성 이스케이프
- flag를 활용하여 탐색: d,g,l,m,s,u,y
- 정규표현식 - 생성방법
  - 리터럴 표기법
    - 평가할때 정규 표현식을 컴파일 한다
    - 정규식이 변하지 않으면, 리터럴 표기법 사용
    - /pattern/flag
  - RegExp 객체
    - 런타임 때 컴파일 된다
    - 패턴이 변할 가능성은 있으나, 알수 없는 데이터에서 가져오는 정규식의 경우 생성자 함수 사용
    - new RegExp(/pattern/, flag)
    - 정적 속성: lastIndex
    - 생성자 함수: RegExp.prototype
    - 인스턴스
      - 속성
        - 적용된 flag 반환: flags
        - 적용된 flag 여부 반환: dotAll, global, ignoreCase, multiline, source, sticky, unicode
      - Method: compile(), exec(), test(), toString(),…
    ***
    - 문자열 인스턴스 method 중 **“찾는”과정이 있는 method**에서 활용한다.
    - 찾아서 일치 하는지 확인: match(정규 표현식), matchAll(정규표현식)
    - 찾는: search(정규표현식)
    - 찾아서 교체하는: replace(정규표현식), replaceAll(정규표현식)
    - 찾아서 분리하는: split(정규표현식)

### Collection

- Collection: 비용을 절감하기 위하여, 상황마다 효율적인 데이터 형태로 처리해야한다
- 컬렉션은 데이터 항목들의 그룹을 의미한다 : 컬렉션에는 list, set, tree, graph 등이 포함되어있다
- 자바스크립트에서는 2가지 타입의 collection이 있다
  - Indexed collections
    - Index 값을 기준으로 정렬되어 있는 데이터 집합 (Array, TypedArray 포함)
    - index로 배열 내의 값을 참조할 수 있다
      - `const ex=[1,2,3]; ex[1];`
  - Keyed collections
    - key값을 기준으로 정렬되어 있는 데이터 집합 - Map, Set 포함
    - 키와 값을 매핑하여 저장한다
    - 저장된 순서대로 각 요소들을 반복적으로 접근할 수 있다
      - `const ex = new Map(); ex.set(key, value)`

### Index collection - Array

- 이름과 인덱스로 참조되어 정렬된 값들의 집합 (인덱스: 색인과 같은 의미)
- 다른 언어와 다르게 자바스크립트는 명시적인 배열 데이터 타입을 갖고 있지 않음
  - 배열 객체를 사용할 수 있다
  - List와 비슷한 객체이며, 순회와 변형 작업을 수행하는 method를 갖는다
- Javascript의 Array객체
  - 0개 이상의 식 expression(배열요소) 목록
  - 배열을 만들때
    - 각 요소로 지정된 값으로 초기화
    - 배열의 길이 (length)는 지정된 요소의 갯수로 결정
      - 길이가 고정되어있지 않다
      - 각 요소의 data type도 고정되어 있지 않다
  - 모든 요소는 필수 값이 아님 (undefined로 지정해도됨)
    - [ ‘apple’, undefined, ‘banana’]
- Array 객체 - 생성 방법
  - 배열 리터럴: 대괄호로 묶는다. []
  - Array 객체 생성자
    - new Array(arrayLength): 길이만 지정된 배열(정수만 가능)
    - new Array(element0,element1,…); 요소가 지정된 배열
- Array 객체 - 특징
  - 배열 요소의 참조:
    - index로 참조, 0부터 시작
    - index값을 속성이름으로 사용하여, 표준 객체의 속성처럼 저장
    - index로 문자열 사용할 수없음, 무조건 정수로만 참조하여 저장
  - 배열에 값 저장: index로 참조하지 않으면 객체의 속성으로 저장됨
  - 배열의 길이 : 마지막 index에 +1 한 값
    - 길이를 지정하는 것 가능
      - 원래 길이보다 작게 지정하면, 배열이 잘림
      - 원래 길이보다 크게 지정하면, 배열 길이는 늘어남
  - 배열의 반복 처리하기
    - for문활용
    - forEach문 활용
- Array 객체
  - 정적 메서드 : from, isArray, of
  - 생성자: Array.prototype
  - 인스턴스
    - 속성: length
    - Method: (일반/순회하며)
      - 요소체크(get): 접근, 찾기, 포함여부, 판별하기
      - 요소변경(set): 추가하기, 제거하기, 변경하기
      - 배열변경(set): 추가하기, 분리하기, 변경하기, 재배치하기
      - 반환타입 변경하기
- Array 객체 - 인스턴스 메서드
  - 요소 check
    - 요소 접근 : at(),
    - 요소 찾기: indexOf(), lastIndexOf(),
    - 요소포함여부: includes()
    - 순회하며
      - 요소확인하기: forEach()
      - 요소판별하기: every(), some()
      - 요소찾기: find(), findIndex()
  - 요소 조작
    - 요소 추가하기: push(), unshift()
    - 요소 제거하기: pop(),shift()
    - 순회하며
      - 요소 변경하기: flatMap(),map()
      - 요소 제거하기: filter()
  - 배열합치기, 추가하기: concat(), fill()
  - 배열 분리하기: slice(),splice()
  - 배열 요소 변경하기: copyWithin(), flat()
  - 배열 재배치하기: reverse()
    - 순회하며 재배치하기: sort()
  - 반환 타입 변환하기
    - 문자열로: join(), toLocaleString(), toString()
    - iterator로: entries(), values()
    - 순회하며 - 타입 변환하기: reduce(), reduceRight()

### key based collection - Map, WeakMap

- key 값을 기준으로 정렬되어 있는 데이터 집합 : Map, Set 포함
- 키와 값을 매핑하여 저장한다
- 저장된 순서대로 각 요소들을 반복적으로 접근할 수 있다
  ```jsx
  const foo = new Map();
  foo.set(key, value);
  ```
- Map 객체와 WeakMap 객체 공통 속성
  - 키와 값을 매핑시켜 저장
  - key는 유니크하다
- Map 객체 특징
  - Map은 간단한 키와 값을 서로 매핑시켜 저장하고, 저장된 순서대로 요소를 반복적으로 접근할 수 있다
  - [key,value]의 형태로 삽입된 순서대로 추가
- Map 객체와 Object 객체의 차이점

  |                            | Object                                                | Map                                                            |
  | -------------------------- | ----------------------------------------------------- | -------------------------------------------------------------- |
  | 속성의 데이터 타입         | string, Symbol 데이터 타입만 가능                     | 모든 값을 키로 활용 가능                                       |
  | default 속성과의 충돌      | Object prototype의 기본속성과 동일한 키를 생성시 충돌 | Map은 기본적으로 갖고 있는 속성이 없어, 기본 속성들과 충돌없음 |
  | 객체의 크기                | 수동으로 추적해야함                                   | size 인스턴스 속성으로 얻을 수 있음                            |
  | 순서보장                   | Object은 순서 보장이 안됨                             | Map은 추가된 순서대로 반복된다                                 |
  | iterable 여부              | Object는 iterable이 아님                              | Map은 iterable                                                 |
  | 퍼포먼스                   | 키, 값 쌍의 빈번한 추가제거에는 퍼포먼스가 좋지 않음  | 키, 값 쌍의 빈번한 추가 제거에는 Map이 퍼포먼스가 좋음         |
  | 직렬화 구문 분석 제공 여부 | 직렬화와 구문 분석 제공(JSON.stringify, JSON.parse)   | Map에서는 제공하지 않고 있다(커스텀으로 구현은 가능)           |

- Map 객체
  - 생성자 함수: Map.prototype
  - 인스턴스
    - 속성: size
    - Method
      - 요소 체크(get): 접근, 포함여부 - get, has
      - 요소 변경(set): 추가하기, 제거하기, 변경하기 - clear, delete, set
      - 순환 관련 - keys, values, entries, forEach
- WeakMap - 특징
  - 키에 대한 강력한 참조를 생성하지 않는 키/값 쌍의 모음
    - 키는 object 만을 허용
  - 객체 정보를 비노출
  - 객체의 정보를 비노출하는 특징을 활용하여 객체의 사적인 정보를 저장하기 위해서 상세 구현 내용을 숨기기 위해서 사용한다
- WeakMap 객체
  - 생성자 함수: WeakMap.prototype
  - 인스턴스
    - 속성: size
    - Method
      - 요소체크(get): 접근, 포함여부 - get, has
      - 요소변경: 추가하기(변경하기), 제거하기 - delete, set
      - 순환관련-없음

### key based collection - Set, WeakSet

- Set와 WeakSet 공통 속성
  - 중복된 값을 허용하지 않는다 - 값이 같은지 검사를 수행한다. same-value-zero-algorithm
  - 배열을 인자로 받을 수 있다
    - 배열의 요소가 Set객체의 요소로 저장됨
    - 중복된 요소가 제거된다
- Set의 특징
  - 모든 값들의 집합(값 콜렉션)
  - 입력된 순서에 따라 저장된 요소를 반복처리 할 수 있다
  - 특정 값은 Set 내에서 하나만 존재
    - NaN은 Set에서 같은것으로 간주된다
  - 배열 > Set으로 Set > 배열로 변환가능하다
  - for…of를 통해 순회가능하다
- Set과 배열의 차이점
  - 포함 여부 확인 퍼포먼스
    - 배열: indexOf를 사용하여 포함 여부 확인은 퍼포먼스가 느림
    - Set: has method를 사용
  - 요소 제거
    - 배열: 배열은 요소를 제거할때 배열을 잘라내야함
    - Set: delete method 사용
  - 요소 찾기
    - 배열: NaN은 indexOf로 포함여부 확인 불가능
    - Set: NaN 포함 여부 확인 가능
  - 중복 여부 확인
    - 배열: 순회하며 확인해야함
    - Set: Set은 값의 유일성을 보장하기 때문에, 중복성 확인할 필요가 없다
- Set 객체
  - 생성자 함수: Set.prototype
  - 인스턴스
    - 속성: size
    - Method:
      - 요소 체크(get): 접근, 포함 여부 - has,
      - 요소 변경(set): 추가하기, 제거하기, 변경하기 - clear, delete, add
- WeakSet의 특징
  - 객체 컬렉션(object 값만을 허용)
    - WeakSet의 인자로 object만 허용
    - 약한 참조를 가진다
    ```jsx
    const foo = new WeakSet();
    foo.add({ foo: 1 });
    ```
- WeakSet객체
  - 생성자 함수: WeakSet.prototype
  - 인스턴스
    - Method:
      - 요소 체크(get): 포함 여부 - has
      - 요소 변경(set): 추가하기(변경하기), 제거하기 - delete, add
      - 순환관련- 없음

### JSON 객체

- JSON (JavaScript Object Notation)
- 인터넷에서 자료를 주고 받을 때 자료를 표현하는 방법으로 알려져 있음
- 키-값 쌍, 배열 자료형, 기타 모든 직렬화 가능한 값 또는 키 - 값 쌍으로 이루어진 데이터 객체를 전달하기 위해 사람이 읽을 수 있는 텍스트를 사용하는 open standard 포맷
- JSON의 파일 확장자 .json
- JSON 형태
  - 기본 자료형 : number, string, boolean, array, object, null
    - 자바스크립트의 문법을 차용
  - 객체의 형태와 유사
- 직렬화
  - 다양한 환경 간에 데이터를 주고 받기 위해 직렬화 작업이 필요하다
  - 직렬화 serialization: Object > 문자열로 변환하는 것
  - 역직렬화 desrialization : 문자열 > Object로 변환하는 것
- JSON 객체
  - 값을 JSON으로 변환하는 method를 제공
  - 생성자 함수 아님
  - 함수로써 사용 불가능
  - 정적 method
    - JSON.stringify: 직렬화 하는 구문
    - JSON.parse: JSON 형태로 파싱하는 구문 (역직렬화)
      - 주의사항 : 문자열이 객체 형태가 아닌 경우 오류 발생
      - try…catch 문으로 에러 핸들링 권장

### 국제화 Intl 객체

- 각 언어에 맞는 문자, 숫자, 시간, 날짜비교를 제공하는 국제화 API를 위한 namespace
  - Intl이라는 namespace로 그루핑하고, 내부에 있는 생성자 속성들
- 정적 method: Intl.supportedLocalesOf();
- 속성
  - DateTimeFormat
  - NumberFormat
- Intl 객체 - DateTimeFormat 생성자 함수 : 언어에 맞는 날짜, 시간 서식을 적용하기 위한 객체
  - 생성자 함수 : Intl.DateTimeFormat.prototype
  - 인스턴스
    - Method:
      - 포맷 결과: format, formatRange
      - 포맷 결과를 각 단위별로 분해하여 배열화: formatToParts, formatRangeToParts
- Intl 객체 - NumberFormat 생성자 함수: 언어에 맞는 숫자 서식을 적용하기 위한 객체
  - 생성자 함수: Intl.NumberFormat.prototype
  - 인스턴스
    - Method:
      - 포맷결과: format, formatRange
      - 포맷결과를 각 단위별로 분해하여 배열화: formatToParts, formatRangeToParts

### 프로토타입과 생성자 함수

- 객체 지향 프로그래밍
  - 객체는 현실의 개념을 추상화하여 정의
    - 상태를 갖고 있고 → this
    - 식별자(속성)을 갖고 있고 → 속성
    - 어떤 행동을 갖고 있다 → 메서드
  - 인스턴스 객체 : 개념의 일원으로써 생성된 객체
  - 객체지향 프로그래밍 : 객체라는 기본단위로 나누고, 이들의 상호작용으로 서술하는 방식
  - 대표적인 객체 지향 프로그래밍
    - 클래스 기반 객체지향 : 자바,, 등
    - 프로토타입 기반 객체지향 : 자바스크립트,,
  - 프로토타입 객체
    - 객체의 인스턴스를 만드는 부모 객체 개념
    - 자바스크립트의 모든 객체는 부모 객체인 프로토타입 객체와 연결
    - 부모객체의 속성과 메서드를 상속받아 사용가능
  - 프로토타입 객체 - 접근하기
    - 모든 객체가 갖고 있는 [[Prototype]] 인터널 슬롯 - [[Prototype]]은 상속을 위해 사용
    - ** proto ** 라는 접근자 속성으로 접근 가능 - ** proto ** 로 Object.prototype 객체에 접근
  - 프로토타입 객체 - 생성하기
    - 함수타입에만 존재하는 prototype 필드
    - 함수에 부모 객체 존재
      - 함수를 활용하여 → 부모 객체의 인스턴스 생성가능
    - **생성자 함수**
      - 인스턴스 객체 생성시 사용
      - 대문자 함수명 컨벤션
      - new 키워드와 함께 호출
    - 인스턴스의 부모 객체 == 생성자 함수.prototype
    - **constructor:** 자기 자신을 생성한 객체 참조

### 프로토타입 chain과 상속

- 프로토타입 chain
  - 객체의 속성 참조시, 속성이 없는 경우 프로토타입 체인 동작
    - [[Prototype]]을 통해서 부모 객체를 탐색
  - 모든 객체의 부모는 Object.prototype
    - End of prototype chain 프로토타입 체인의 종점
  - 만약 마지막 부모 객체(Object.prototype)에서까지 속성을 찾지 못할 경우, undefined 반환
- 프로토타입 객체의 확장과 상속
  - prototype 객체 속성과 메서드 정의시 인스턴스 객체에서 부모 메서드와 속성을 참조
  - 객체와 프로토타입에 동일한 이름의 속성이나 메서드가 있는 경우
    - 객체의 속성이 먼저 참조
    - property shadowing: 프로토타입 속성이 가려지는 현상
    - method overriding: 프로토타입 메서드가 가려지는 현상

### class 문법

- class의 형태
  - class 클래스명 {…}
  - class 내에는 메서드만 작성가능
  - 인스턴스 생성 : new 클래스명();
- class 문법
  - constructor 특수 메서드
  - method
    - 인스턴스 method
    - 정적 method
  - 인스턴스 속성
    - 조회 및 조작
    - 할당 및 조작
  - 클래스 상속
- class 문법 - constructor
  - 인스턴스를 생성하고, 클래스 필드를 초기화 하기 위한 약속된 특수 메서드
    - 인스턴스가 생성될때, 호출되는 메서드
  - 인스턴스 생성시 전달한 인자를 constructor 메서드의 인자로 받을 수 있다
  - constructor는 생략 가능
- class 문법 - 인스턴스 method
  - 클래스 내에 존재하는 method
  - method 내에서 클래스를 this로 접근 가능
  - 클래스의 인스턴스 속성에도 접근 가능
- class 문법 - 정적 메서드
  - 클래스의 인스턴스를 생성하지 않아도 호출할 수 있는 메서드를 정의할때 사용
  - static 키워드 사용
  - util 용의 함수를 정의할 때 사용
- class 문법 - 인스턴스 속성
  - 클래스 내부에 캡슐화된 변수 == 멤버 변수
  - this에 추가한 속성
  - 인스턴스 속성은 this에 바인딩 필요
  - 속성은 인스턴스 생성 이후 바로 참조가능해야하므로, 인스턴스 속성 초기화는 constructor 메서드에서 보통 진행
- class 문법 - 인스턴스 속성 조회 및 조작
  - getter : 특정 인스턴스 속성을 조회하며 조작 하는 메서드
    - 형태 : 메서드 이름앞에 get 키워드 사용, getter 메서드는 무조건 값을 반환
    - 사용시, 일반 메서드처럼 호출하지 않고 속성처럼 참조하는 형식으로 사용
- class 문법 - 인스턴스 속성 할당 및 조작
  - setter : 특정 인스턴스 속성에 할당하며 조작하는 메서드
  - 형태 : 메서드 이름 앞에 set 키워드 사용
  - 사용시, 일반 메서드처럼 호출하지 않고 속성처럼 할당하는 형식으로 사용
- class 문법 - 상속 - extends
  - 코드의 재사용 관점에서 상속 필요(부모-자식)
  - extends와 super 키워드를 통해 class에서 상속구현
  - extends
    - 부모클래스를 상속받는, 자식 클래스를 정의할때 사용
  - `class 부모 {…}`
  - `class 자식 extends 부모 {…}`
- class 문법 - 상속 - super 키워드
  - super()
    - 부모 클래스의 생성자를 호출하게 됨
    - 부모 클래스의 인스턴스 속성을 바인딩함
    - 자식클래스의 생성자가 this에 접근하고 수정가능
  - 자식 클래스의 constructor 사용시 constructor 반환문 전에 사용되어야 함

### 자바스크립트 컨텍스트 - this와 화살표 함수

- this란?
  - 컨텍스트 참조가능한 키워드(전역 Context, 함수 Context)
    - 객체를 참조하는 역할, 어떤 객체인지 동적으로 결정됨
  - 함수 Context
    - 함수가 호출될때, 매개변수로 this가 암묵적으로 전달
    - 함수 호출방식에 따라 this에 바인딩되는 객체가 상이
    - ES6 화살표 함수: this 바인딩 제공하지 않음
  - 함수 호출 방식
    - 함수호출, 객체의 메서드 호출, 생성자 함수 호출, apply, call, bind로 호출
- this 바인딩 - 함수 호출 방식
  - 전역 객체에서 this 사용시
    - Browser-side: window
    - Server-side: global
  - 함수 내부에서 this는 전역객체에 바인딩
  - 함수에 내부함수 존재 시에도 this는 전역객체에 바인딩
  - 객체의 메서드 내에 내부함수가 있을 경우, 함수 호출방식으로 취급되어 전역객체를 바라봄
    - 이를 해소하기 위해서 this를 다른 변수에 저장하고 사용하거나 , 내부함수를 해당 객체에 bind
- this 바인딩 - 객체 메서드 호출방식
  - 메서드 내부의 this는 해당 메서드를 호출한 객체에 바인딩
  - 프로토타입 객체의 메서드도 동일하게 해당 메서드를 호출한 객체에 바인딩
- this 바인딩 - 생성자 함수 호출 방식
  - 생성자 함수 호출시 아래와 같은 순서로 동작
    1. 빈 객체 생성, this 바인딩 : this는 빈 객체에 바인딩
    2. this로 속성 생성: this를 사용하여 동적으로 속성과 메서드 생성
    3. 생성된 객체 반환: 반환문이 없어도 1번에서 생성되었던 객체가 반환됨
- this 바인딩 - apply, call, bind 호출 방식
  - this를 명시적으로 바인딩 하는 방법
  - Function.prototype.apply
  - Function.prototype.call
  - Function.prototype.bind
- this 바인딩 - apply, call
  - 함수명.apply(바인딩할 객체, [함수호출시 넘기는 인자들]), 함수명. call(바인딩할 객체, 함수호출시 넘기는 인자1,…)
    1. 함수내의 this에 바인딩할 객체가 바인딩 됨
    2. 함수에 인자들이 전달됨
    3. 함수호출됨
  - 바인딩과 동시에 함수를 호출한다
- this 바인딩 - bind
  - 함수명.bind(바인딩할 객체)
    1. 함수 내의 this에 바인딩할 객체가 바인딩
    2. 바인딩된 함수 반환
  - apply와 차이점: 바인딩과 함수 호출이 분리
- this 바인딩 - 화살표 함수
  - ES6의 화살표 함수
    - 함수를 선언할때, this에 바인딩할 객체가 정적으로 결정
    - 항상, 상위 스코프 this를 가리킴 (Lexical this)
  - 화살표 함수의 형태: 익명 함수 형태
    - (인자들) ⇒ {…}
  - 지양해야하는 사용형태
    - 객체의 메서드( + prototype 메서드)
    - 생성자 함수: prototype 객체 없음

### 자바스크립트 컨텍스트 - Scope

- 프로그래밍에서 Scope
  - 스코프 == 변수 영역
  - 변수가 유효성을 갖는 영역
  - 스코프의 규칙 : 렉시컬 스코프 규칙, dynamic 스코프 규칙
  - 스코프의 종류 : 전역, 모듈, File, 함수, 블록, …
- Scope의 규칙 : 변수 영역을 지정하는 규칙
  - 정적 영역 규칙 - lexical scoping rule
    - 정적 영역 규칙 static scoping rule (lexical scoping rule)
    - 어디서 호출하였는지가 아니라, 어디에 선언하였는지에 따라 스코프 결정(소스코드 구조 기준)
    - 자바스크립트는 lexical scoping rule을 따름
  - 동적 영역 규칙 - dynamic scoping rule
    - 어디서 호출하였는지에 따라 스코프 결정
    - 런타임때 결정됨
- Scope의 종류 : 전역, 모듈, file, 함수, 블럭 스코프
  - 전역 스코프: 소스 코드상의 모든곳에서 사용할 수 있는 전역 변수
    - 자바스크립트: (브라우저 기준) window 객체
  - file 스코프
    - 해당 파일 전체에서 접근 가능, 다른 파일에서 접근 불가능
    - 원시적인 형태의 모듈 영역
    - ES6+자바스크립트: `<script type= “module” …>` 로 조회되는 파일
  - 모듈 스코프 : 모듈을 지원하는 프로그래밍 언어에서 모듈 단위 변수 선언 가능
  - 함수레벨 스코프
    - 지역 변수: 함수내에서 유효한 변수
      - 함수가 반환된 이후에는 사용 불가능
      - 함수 외부에서 유효하지 않음
    - 자바스크립트는 기본적으로 함수 레벨 스코프
  - 블록레벨 스코프
    - 지역변수: 코드 블럭 내에서 유효한 변수
    - ES6 + 자바스크립트: let, const 키워드는 블록레벨 스코프
- 자바스크립트의 Scope
  - 스코프 규칙 : lexical scoping rule
  - 스코프 종류
    - 함수 레벨 스코프 기반
    - 전역 스코프 :전역 객체 window의 속성(브라우저 기준)
    - ES6+ 부터 지원하는 스코프
      - 블록레벨 스코프: let, const 키워드는 블록레벨 스코프,
      - file 스코프 : `<script type= “module”…>` 로 조회되는 파일

### 자바스크립트 컨텍스트 - 실행 컨텍스트

- 자바스크립트를 실행하기 위한 정보 : 변수, 함수 선언, 변수의 유효범위(스코프), this
- ⬇️ 물리적 객체 형태로 관리 ⬇️
- 실행 컨텍스트: 코드가 실행되는 범위에 대한 개념
- 실행 컨텍스트의 생성 단계 - Creation Phase
  - 코드 평가 단계: Lexical Environment 생성
  - 함수와 변수를 기록
    - 선언 정의, 객체 정의
    - this 바인딩: 함수 호출 여부에 따라 달라짐
  - 외부 환경 참조: 스코프 체인이 형성됨
- 실행 컨텍스트의 실행 단계 - Execution Phase
  - 코드 실행 단계: 위에서 아래로 코드가 실행
  - 변수는 값이 할당
  - 함수 실행 코드가 있을 경우, 함수 실행
    - 새로운 함수 실행 컨텍스트 생성 및 함수 실행
- 실행 컨텍스트의 3가지 종류
  - global 컨텍스트 == 전역 컨텍스트
    - 함수 내에서 실행되는 코드가 아니라면, 전역 컨텍스트에서 실행
    - e.g 브라우저 기준: Global object = window
  - functional 컨텍스트
    - 함수가 호출될때마다, 함수에 대한 실행 컨텍스트 생성
    - 각 함수들은 자신만의 실행 컨텍스트 존재
  - eval 컨텍스트 : eval 함수 만의 실행 컨텍스트 존재
- 자바스크립트의 Call Stack : 자바스크립트 엔진이 호출된 함수와 순서를 추적하는 방법
  - 어떤함수가 동작하고 있는지, 다음에 어떤 함수가 호출되어야 하는지 등을 제어
  - 함수가 반환된 후 실행이 올바른 지점에서 다시 선택되도록 한다
    - == 함수 호출을 수행할 수 있게 해주는 Record 보관 구조
  - stack 자료구조: 프레임이 쌓이는, Last in First out (LIFO) 형태의 자료구조
  - 콜스택: 함수 호출시 만들어지는 실행 컨텍스트가 쌓임
    - 하나의 일만 처리 가능
  - 자바스크립트 엔진은 코드를 평가하여 실행 컨텍스트를 만들어 → 콜 스택에 하나씩 쌓고 콜스택에서 실행 컨텍스트를 실행하며 → stack에서 하나씩 없앤다
- 정리
  - 실행 컨텍스트: 자바스크립트를 실행시키기 위해 필요한 정보를 객체 형태로 추상화 한것
  - 실행 컨텍스트의 단계
    1. 생성 단계 : Lexical Environment 변수/함수 선언 매핑, 외부 환경 참조, …
    2. 실행 단계
  - 실행 컨텍스트의 3가지 종류: Global Context, Functional Context, eval Context
  - 자바스크립트의 콜스택
    - 호출된 함수와 순서를 추적 할 수 있는 구조
    - 스택 자료 구조: LIFO

### 자바스크립트 컨텍스트 - 클로저

- 함수가 종료가 되었는데, 아직 참조가 남아있는 경우
  - 자바스크립트: 일급객체
  - 함수 내의 내부 함수
  - 발생 조건
    - 외부함수 실행 컨텍스트 환경의 변수를 참조하고 있는 내부함수 실행 컨텍스트
  - 상황
    - 내부 함수내에서 아직 외부함수의 변수를 참조하고 있어, 외부함수가 종료되었지만, 외부함수의 참조가 유지되어, 외부함수 환경에 접근할 수 있는 상황
- 클로저: 반환된 내부함수가 자신이 선언됐을때의 환경인 스코프를 기억하여 자신이 선언됐을때의 환경 밖에서도 호출되어도 그 환경에 접근할 수 있는 함수
- 클로저 특징
  - 함수가 종료되어도, 스코프를 기억
  - 특정 스코프에 접근할 수 있는 함수
  1. 상태유지
  2. 은닉화

## [Feelings+Finding]

- 이번 데이터 처리 객체와 빌트인 객체 그리고 매커니즘 파트 강의는 양도 많고 처음 배우는 개념이 많아서 살짝 버거운 면이 없지 않았다... 완벽히 이해한 것이 아니기 때문에 복습을 해야겠다는 생각이 들었다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
