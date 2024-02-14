---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(1/8)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 1월 8일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til10

toc: true
toc_sticky: true

date: 2024-1-8
last_modified_at: 2024-1-8
---

## [Facts]

- javascript 연산자, flow control 에 대해서 공부함

## [TIL]

### 데이터 처리 : 연산자

연산자: 하나 이상의 표현식을 대상으로 연산을 수행하여 하나의 값을 만든다

1. **단항 연산자 : 하나의 피연산자만 사용하는 연산**
   - void: 표현식을 평가할때 값을 반환하지 않도록 지정
   - typeof: 평가 전의 피연산자 타입을 나타내는 문자열을 반환
   - delete: 객체의 속성을 삭제한다
2. **산술 연산자 : 두 개의 숫자값을 피연산자로 받아서 하나의 숫자값을 반환**
   - **단항 산술 연산자**: 1개의 피 연산자를 산술 연산하여 숫자값을 반환
     - ++: 숫자 1을 증가시키고, 증가시킨 값을 암묵적으로 할당
     - --: 숫자 1을 감소시키고, 증가시킨 값을 암묵적으로 할당
     - +: 양수의 표현, 아무런 효과 없음
     - -: 양수를 음수로, 음수를 양수로 반전시킨 값을 반환
     - 증가/감소 연산자: 위치에 따라 처리 단계 상이
     - 전위 증가감소 연산자: 피연산자 앞에 위치(++피연산자)
     - 후위 증가감소 연산자: 피연산자 뒤에 위치(피연산자++)
   - **이항 산술 연산자**: 2개의 피 연산자를 산술연산하여 숫자값을 반환
     - -
     - -
     - -
     - /
     - %(나머지)
3. **관계 연산자: 피연산자를 비교하고, 결과가 참인지에 따라 boolean 값을 반환한다**

   - in : 객체 내에 속성이 존재할 경우 true반환
   - instanceof: 특정 객체 타임에 속하면 true를 반환

   ```jsx
   const animal = {
   	name = "dog"
   };
   'name' in animal; // true
   animal instanceof Object; // true
   ```

4. **비교 연산자 : 피연산자를 비교하고, 결과가 참인지에 따라 boolean값을 반환한다, 피연산자에는 숫자, 문자열, 논리형, 객체타입**
   - ==(동등 연산자): 서로 같으면 true
   - ===(일치 연산자): 서로 같고, 타입도 같으면 true
   - !=(부등 연산자): 서로 다르면 true
   - !==(불일치 연산자): 서로 다르고, 타입도 다르면 true
   - \>
   - ≥
   - <
   - ≤
5. **논리 연산자**
   - 두개의 피연산자 중 하나를 반환
   - 반환되는 값이 무조건 Boolean값이 아니다
   - 단축평가 논리: 첫번째 식을 평가한 결과에 따라서, 두번째 식 평가를 실행
   - A && B (AND 연산자): A가 false로 평가되면 A를 반환한다, A가 true로 평가되면 B를 반환한다
   - A || B (OR 연산자): A가 false로 평가되면 B를 반환한다. A가 true로 평가되면 A를 반환한다
   - null, undefined, 빈문자열 → false로 평가
   - AND 연산자: null 검사에 활용
   - OR 연산자: 캐싱 값에 대해서도 사용
6. **기타연산자**

   - 쉼표 연산자: 두 연산자를 모두 평가한후, 오른쪽 피연산자의 값을 반환
   - 문자열: 두 문자열 값을 서로 연결하여 새로운 문자열을 반환
   - 옵셔널 연산자: 객체의 속성을 참조시, 유효하지 않는 경우, 에러를 발생시키지 않고 undefined를 반환

   ```jsx
   const num = (3, 4);
   a; // 4
   "통학은" + " " + "힘들다"; // '통학은 힘들다'
   const animal = { name: "puppy" };
   animal.age?.puppy;
   ```

   - 할당 연산자: 오른쪽 피연산자가 왼쪽 피연산자에 값을 할당한다
     - +=
     - -=
     - \*=
     - /=
     - %=
     - \*\*=
     - &&= (논리 AND 할당)
     - ||= (논리 OR 할당)
   - 삼항 연산자: 조건 연산자에 따라 두 값중 하나를 반환한다
     - condition ? trueValue : falseValue

### 데이터 처리 : 함수

- **함수: 소프트웨어에서 특정 동작을 수행하는 코드 일부분을 의미**
- 외부 코드가 호출할 수 있는 하위 프로그램

  ```jsx
  let hyunjiAge = 24;

  function addAge(age) {
    return age + 1;
  }
  addAge(hyunjiAge); // 25
  // 함수 외부에서 addAge를 호출
  // 자바스크립트에서는 괄호를 사용하여 호출 함수명()
  ```

- 함수의 형태
  - input: 로직 처리를 위해 주입 받는 데이터
  - output: 로직 처리후 반환되는 결과 데이터
  - 본문: 명령문의 시퀀스로 구성
- JavaScript의 함수

  - 자바스크립트에서 함수는 객체처럼 **속성과 메서드**를 가질 수 있다
  - **객체와의 차이점은 함수는 외부에서 호출이 가능하며, 객체는 외부에서 호출이 불가능하다**

  ```jsx
  const 객체 = {
    속성: "값",
    메서드: function () {
      return "wow";
    },
  };

  함수(); // 'wow'
  객체(); // TypeError
  ```

  - 자바스크립트에서 함수는 일급객체의 특징을 모두 갖고 있다

    - **_자바스크립트 함수는 함수의 실제 매개변수가 될수 있다_**

      ```jsx
      function ex1(input) {
        return input() + 5;
      }

      function ex2() {
        return 3;
      }

      ex1(ex2); // 8
      ```

    - **_자바스크립트 함수는 함수의 반환값이 될 수 있다_**

      ```jsx
      function ex1(input) {
        return input()() + 5;
      }

      function ex2() {
        return 3;
      }
      function ex3() {
        return ex2;
      }

      ex1(ex3); // 8
      ```

    - **_자바스크립트 함수는 할당명령문의 대상이 될 수 있다_**
    - **_자바스크립트 함수는 동일 비교의 대상이 될수 있다 (값으로 표현가능)_**

      ```jsx
      const ex1 = function () {
        return 3;
      };

      ex1(); //3
      ```

  - 일급객체란, 다른 객체들에 일반적으로 적용가능한 연산을 모두 지원하는 객체를 가리킨다

- 함수의 형태

  - **함수 이름**: 함수의 이름. (외부에서 호출시 이름이 사용된다)
  - **매개 변수**: 함수에 전달되는 인수, 유사배열 형태

    - **_기본값 매개변수_**: 매개변수 값이 없거나, undefined가 전달될 경우 대체되는 초기값, 매개변수에 할당연산자와 함께 초기값을 할당

    ```jsx
    function ex1(age = 24) {
      return age;
    }

    ex1(); // 24
    ```

    - **_나머지 매개변수_**: 가변항 함수, spread 연산자

    ```jsx
    function ex2(arg, ...rest) {
      console.log(rest); // ['b','c']
      return arg;
    }

    ex2("a", "b", "c"); // 'a'
    // 첫번째 인자는 argument로 할당이 된다
    ```

    - **_arguments 객체:_** 함수에 전달되는 인자들을 참조할 수 있는 객체

      - 자바스크립트의 함수: Function 객체 상속
      - Function 객체의 기본 속성: arguments
      - 형태: 배열이 아니고 유사 배열 형태
        - 배열 내장 method 사용 불가

      ```jsx
      function ex(arg) {
        console.log(arguments);
      }

      ex(1, 2, 3, 4);
      // arguments 객체가 정의되어있지 않지만 조회가 되는 이유는 function builtin 객체로 프로토타입 체인을 통해서 참조할 수 있기 때문에 출력이 됨
      ```

  - **함수 몸체**: 명령 시퀀스들이 존재하는 블록

- 매개변수(parameter)와 인자(argument)의 차이
  - 매개변수: 함수를 정의할때 사용하는 변수
  - 인자: 함수가 호출될때 넘기는 값
- 함수 생성 방법

  - **함수 선언문**
    ```jsx
    function ex() {
      console.log("hi");
    }
    ex(); //'hi'
    ```
  - **함수 표현식:** 함수를 익명함수로 정의를 하고 익명함수를 변수에 담아서 표현을 한것

    - 익명함수 : 함수명 생략
    - 기명함수

    ```jsx
    const ex = function () {
      console.log("hello");
    };

    ex(); //'hello'
    ```

  - **Function 생성자 함수**
    - Function 객체: 자바스크립트 내장 객체 중 하나
    - 함수 생성방법의 기본 원리
      - 함수표현식, 함수선언문: 축약법
    - 생성자 함수
      - 내장 객체 활용: 인스턴스 생성
      - new 내장 객체()
    - new Function (arg1, arg2, …, ‘return 1’)
    ```jsx
    const ex = new Function("console.log('hi')");
    ex();
    ```
  - **화살표 함수 표현식**

    - function 키워드 사용하지 않고, 화살표 사용(⇒)
    - 익명함수
    - const 변수명 = (arg, …) ⇒ {return …}

    ```jsx
    const ex = (arg) => {
      return arg();
    };

    ex(() => {
      return 5;
    }); //5
    ```

    ```jsx
    const ex2 = () => {
      console.log("hi");
    };

    ex2();
    ```

- 함수 사용 패턴

  - **IIFE(즉시 실행함수)**
    - 함수 정의와 동시에 실행
    - 코드 평가 → 코드 실행 → 최초 1회 실행(초기화 처리에 주로 사용됨)
    - 작성방법: 즉시 실행할 함수 괄호로 감싸기, 괄호로 감싸진 함수를 수행
    ```jsx
    (function () {
      return 5;
    })(); // 5
    ```
  - **재귀함수**

    - 자기 자신을 호출하는 함수
    - 계속 자신을 참조하여 호출하므로, 무한히 호출될 수 있음 (탈출 조건을 함수 초반에 정의해야함), 직관성이 떨어질수 있어, 한정적 사용 권장

    ```jsx
    function ex(arg) {
      if (arg === 5) return arg; // 탈출 조건

      console.log(arg);
      ex(arg + 1);
    }

    ex(0);
    ```

  - **중첩함수**
    - 내부 함수
    - 내부 함수 내의 변수 참조 → 부모를 포함한 외부 범위 참조 가능
    - 부모 함수 내의 변수 참조 → 자식 범위 참조 불가능
    - 스코프 체인
    ```jsx
    function ex(arg) {
      function ex2() {
        console.log(arg);
      }
      ex2();
    }
    ex(2); // 2
    ```
  - 콜백함수: 함수의 매개변수에 넣어지는 함수를 콜백함수라고 함

    - 함수의 매개변수가 될수 있다(일급 객체중)
      - 인자로 B함수를 받은 A함수
      - A함수가 호출되는 시점에 B함수도 호출
    - 특정 이벤트가 발생했을때
      - 시스템에 의해 호출되는 함수

    ```jsx
    const ex = (arg) => {
      return arg();
    };

    ex(() => {
      return 3;
    }); // 3
    ```

    ```jsx
    function ex(arg) {
      arg();
    }

    ex(() => {
      console.log(3);
    }); // 3
    ```

### 데이터 처리 - flow control

- Flow control(제어흐름, 흐름제어): 명령형 프로그램의 개별 명령문, 명령 또는 함수 호출이 실행되거나 평가되는 순서
- 5가지 제어흐름의 종류
  1. goto: 다른 구문에서 시작 - 개발 설계에 오류를 발생시킬수 있으므로 권장하지 않는 방법
  2. **choice**: 일부 조건이 충족되는 경우에만 일련의 명령문 실행
     - If-else, switch
  3. **loop:** 어떤 조건이 충족될때까지 일련의 명령문을 0회 이상 실행
     - Collelction loop, General loop
  4. **continue**: 현재 실행 구문에서 떨어진 한 구문의 집합을 실행
     - Loop continuation
  5. **break:** 프로그램 실행을 중단
     - Loop early exit, 함수 실행 정지
- 표현식과 문의 개념
  - **표현식 : 어떤 값으로 이행되는 임의의 유효한 코드 단위**
    - 표현식이 평가되면, 새로운 값을 생성하거나 기존 값을 참조
    - 값으로 평가될 수 있는 문은 모두 표현식
    - 리터럴 표현식, 함수 표현식,…
  - **문 : 프로그램을 구성하는 기본 단위, 최소 실행 단위 == 명령문**
    - 선언문, 할당문, 제어문, 반복문, 블럭문, …
    - 블럭문: 명령문들을 그룹으로 묶을 수 있는 블럭문, 한쌍의 중괄호로 묶어서 표현
    - 제어문: choice(If..else, switch), Loop(Loop early exit-break, Loop continuation-continue), Subroutine exit(return), Non-local control flow(try…catch, throw, generator, async)
- 조건문: 일부 조건이 충족되는 경우에만 일련의 명령문 실행 (If…else문, switch문)
  - If…else문: if문의 논리 조건에는 true, false로 평가할 수 있는 표현식을 대입가능
    - 해당값은 false로 평가(Falsy): false, undefined, null, 0, NaN, “”(empty string)
    - else if 절을 사용하여 다수의 조건을 순차적으로 검사할 수 있음
    - Nested Conditional: 실제 로직을 구현할때, 중첩 if문을 사용할 수 있음 - 마틴 파울러의 리팩토링 자료: nested conditional 지양, Guard Clauses 형태로 구현
  - switch 문: switch에 명시된 표현식을 평가한 후, 평가된 값과 case라벨 값을 비교하여 일치하는 case의 명령문을 실행
    - default 작성: 평가된 값에 해당하는 case 문이 없을 경우 default의 명령문이 실행되도록
    ```jsx
    switch (표현식) {
    	case 라벨:
    		...명령문...
    	default:
    		...명령문...
    }
    //default문은 라벨없이 작성한다
    ```
- Loop - 반복문

  - 조건부 loop
    - 시작할때 조건을 평가하는 타입: 본문 생략 가능 - **while 문**
    ```jsx
    while (표현식) {
    	...명령문...
    }
    ```
    - 마지막에 조건을 평가하는 타입: 본문은 항상 한번 이상 실행 - **do…while문**
    ```jsx
    do {
    	...명령문...
    } while(표현식);
    ```
  - for loop : 특정 부분의 코드가 반복적으로 수행될 수 있도록 한다

    - [초기화-조건식-증감문]의 형식: while 문과 다르게, 해당 루프와 관련된 loop변수가 존재
      - loop 변수의 비교 및 증감을 위한 별도 문법을 명시 필요
      - == loop 변수를 활용하여 명시적으로 카운트를 관리 필수
      ```jsx
      for([초기문];[조건문];[증감문];){...}
      // 초기문: loop 내에서 사용할 loop 변수를 초기화
      // 조건문: loop 내 코드 실행전, 조건을 평가하여 loop를 지속할지 판단
      // 증감문: loop 내 코드 실행후, 실행되는 문장(루프 변수 증감 용도)
      ```
    - 집합 loop 형식(Foreach loop) : 컬렉션 안의 항목들을 횡단하는 제어흐름문

      - for문과 다르게, 명시적으로 카운터(루프변수)를 관리 하지 않는다
      - 잠재적인 순환 횟수 오류를 예방한다.(off-by-one error) - 코드를 더 단순하게 읽힐 수 있게 해준다
      - **for…of 문** : 반복가능한 객체를 통해 반복하는 루프를 만든다

      ```jsx
      for([변수] of [object]){...}
      // 변수는 반복 가능한 객체의 값을 반환한다
      // 반복가능한 객체 : Array, Set, String,..
      ```

      ```jsx
      const animal = "puppy";

      for (const i of animal) {
        console.log(i);
      }

      // 'p' 'u' 'p' 'p' 'y'
      ```

      - **for…in 문** : 객체의 열거 속성을 통해 지정된 변수를 반복한다

      ```jsx
      for([변수] in [object]){...}
      // 변수는 객체의 key값을 반환한다
      ```

      ```jsx
      const animal = {
        puppy: "🐶",
        kitty: "🐱",
      };

      for (let key in animal) {
        console.log(key);
      }
      //'puppy' 'kitty'
      ```

- break문, continue 문
  - break문 : 제어흐름의 종류 중 프로그램 실행 중단 종류
    - 반복문, switch 문을 종료시킬때 사용
    - 가장 가까운 while, do-while, for, switch문을 종료하고, 다음 명령어로 넘어간다
  - continue문 : 제어흐름의 종류 중 현재 실행 구문에서 떨어진 한 구문의 집합을 실행 종류에 속한다
    - while, do…while, for문을 다시 시작하기 위해 사용한다
    - 가장 안쪽의 while, do-while, for 문을 둘러싼 반복을 종료하고, 다음 loop를 실행한다
    - 전체 루프 실행을 종료하지 않는다
      - while: 조건문으로 이동
      - for: 증감문으로 이동
- 예외처리하기

  - 예외의 종류
    - ECMAScript Error: 자바스크립트 언어에서 발생하는 Error Type
      - RangeError: 값이 집합에 없거나, 허용 범위가 아닐때
      - ReferenceError: 존재하지 않는 변수 참조시
      - SyntaxError: 문법을 지키지 않았을때
      - TypeError: 값이 기대한 자료형이 아니여서 연산이 불가능할때
      - …
    - DOMException: Web API 레벨에서 발생하는 Error Type
      - NetworkError: 네트워크 에러 발생시
      - AbortError: 작업이 중단되었을때
      - TimeoutError: 작업 시간이 초과되었을때
      - …
    - 그외 예외 : 개발자가 직접 예외 상황을 예상하여 핸들링 할 수 있다, 자바스크립트의 Error 객체를 사용하여 직접 에러를 정의내리고 핸들링 할 수 있다
  - throw 문 : 예외를 발생시킬때 사용 - catch블럭에서 에러 객체 핸들링

    - 예외가 발생하면 1. 현재함수의 실행이 중지 2. 에러 객체와 함께 에러가 throw 3. 제어흐름은 호출자 사이에 catch블록이 있으면, catch 블록으로 전달 / 호출자 사이에 catch 블록이 없으면, 프로그램 종료
    - throw문 이후의 명령문은 실행되지 않는다

    ```jsx
    const ex = () => {
      console.log(3);
      throw "hi";
      console.log(2);
    };

    ex();
    ```

  - Error 객체

    - 사용자가 직접 Error 객체를 정의하여 사용할 수 있다. - new Error( ‘에러메시지’), Error.message, Error.name
    - ECMAScript 표준 내장 오류 유형이 있다

    ```jsx
    const ex = () => {
      console.log(1);
      const customError = new Error();
      customError.name = "ErrorName";
      customError.message = "에러가 발생함";

      throw customError;
      console.log(2);
    };

    ex();
    ```

  - try-catch문 : 에러를 catch하여 프로그램이 종료되지 않도록 해야함, 예외처리를 담당하는 핸들러를 찾기위해, 순서대로 콜스택을 거슬러 올라가 올바른 핸들러를 찾아내어 그곳에서 처리되도록 한다
    - Call stack : 자바스크립트 코드가 실행되며 생성되는 실행컨텍스트를 저장하는 자료구조, 함수를 호출할때 마다 스택이 쌓이고, 함수의 실행이 종료되면, 콜스택에서 스택을 제거하는 원리
    - 에러 throw 되면 콜스택을 확인하여, 핸들링하고 있는 catch문이 있는 스택에서 처리
    - try 블록의 명령문 중 하나가 실패하면, catch로 제어권이 넘어가고 명령문 중 하나가 성공하면, catch로 제어권이 넘어가지 않는다
    - catch 블럭에서 인자로 throw된 catchID를 참조할 수 있다
    ```jsx
    try{...}
    catch(catchID){...}
    ```
    - 콜스택 중 하나에서 catch문에서 예외가 처리된다면, 더 상위의 콜 스택에서는 더이상 예외가 타고 올라오지 않는다
    - try…catch문의 finally 블록: finally 블록은 try 블록에서 예외 상황이 발생하지 않더라도, 실행된다
    - try…catch문 사례: 외부에 의존 되어서 구현된 로직에서 사용
      - network 에러 발생시
      - 에러를 감지해야 하는 비즈니스 로직 : 비즈니스 데이터가 유효하지 않는 경우
      - 유저가 잘못된 데이터를 입력한 경우

## [Feelings+Finding]

- 자바스크립트에서 함수는 변수에 할당될 수 있고, 함수의 인자로 전달될 수 있다. 또한 함수의 반환값으로 사용될수 있으며 런타임에 생성될 수 있다. 이러한 특징을 가지고 있기 때문에 함수가 일급객체로 취급된다.

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
