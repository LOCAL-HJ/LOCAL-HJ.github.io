---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(2/2)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 2월 2일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til18

toc: true
toc_sticky: true

date: 2024-2-2
last_modified_at: 2024-2-2
---

## [Facts]

- 리액트 기초

## [TIL]

### Why React?

- 중복 코드 작성 >> Shotgun Surgery(산탄총 수술)
- Shotgun Surgery를 안해야 하는 코드를 작성해야 함
- 컴포넌트화 방식 - 공통적으로 다른페이지에서도 써야하는 요소들을 컴포넌트로 만들어서 사용하는것 >>> Shotgun Surgery를 할 필요가 없어짐

1. **React는 Component 기반의 UI 라이브러리**
2. **React는 선언형 프로그래밍 방식으로 웹서비스를 설계**
   - 명령형 프로그래밍: 절차를 하나하나 다 나열해야함
     ```
     1. 결과를 표시할 요소를 가져온다 (id = result)
     2. 현재 결과값을 10진수 기준, 숫자형으로 변환해서 가져와 current라는 상수에 저장한다
     3. Current 상수에 저장된 값을 결과를 표시할 요소의 값에 plus라면 +1해서 넣고,
     	 minus라면 -1해서 넣는다

     // jQuery
     ```
   - 선언형 프로그래밍: 그냥 목적을 바로 말함
     ```
     1. plus를 누르면 , result 값에 +1 한다. Minus를 눌렀다면 반대로 한다

     // react
     ```
3. **Virtual Dom**
   - DOM(Document Object Model) : 브라우저가 실제로 사용하는 객체
   - 화면에 나타나는 DOM 을 업데이트 시키는 것이 아니라 가상의 DOM을 미리 업데이트 시켜본 다음에 가상의 DOM이기 때문에 렌더링 과정은 안거침, 따라서 그만큼의 연산은 안함, 한번에 Real DOM에 업데이트
   - 5번을 업데이트 할것을 한번에 업데이트 할 수 있게끔 함
       <img width="837" alt="4" src="https://github.com/LOCAL-HJ/LOCAL-HJ.github.io/assets/107786171/5e58e494-c1a0-4da4-a114-938feeec4a15">


### Create React APP

- **React.js**: Node 기반의 Javascript UI 라이브러리
- **Webpack**: 다수의 자바스크립트 파일을 하나의 파일을 하나의 파일로 합쳐주는 모듈 번들 라이브러리
- **Babel**: JSX등의 쉽고 직관적인 자바스크립트 문법을 사용할 수 있도록 해주는 라이브러리
- **_Boiler Plate: 이미 세팅 완료된 패키지_**

---

- create react app 도 npm에 올라가 있는 패키지 이기 때문에 기본적으로 `npm i` 설치해서 사용해야하지만 create react app 을 한번 쓰고 말것이기 때문에 npx 를 사용
  - **npx** : npm을 편리하게 사용하기 위한 도구, 설치되어 있지 않은 패키지를 한번만 사용하고 싶을때 사용
  - `npx create-react-app 프로젝트명`
  - localhost:3000 이라는 주소는 자신의 컴퓨터를 가리키는 주소 , 크롬 웹브라우저가 pc에 요청을 날렸고 컴퓨터는 react app을 반환
    - npm start 명령어를 이용해서 리액트 앱을 실행시킨 순간 컴퓨터는 웹 서버가 됨. 웹 브라우저에서는 내 컴퓨터의 주소로 웹사이트에 접속할 수 있게 됨
    - 리액트 앱은 nodejs 기반의 웹 서버위에서 동작하고 있다
- `npm i` : node module 다시 다운받을 수 있음

```jsx
import "./App.css";

function App() {
  let name = "이름";

  return (
    <div className="App">
      <header className="App-header">
        <h2>안녕 {name}</h2>
      </header>
    </div>
  );
}

export default App;
// app.js
// export default는 한개만 내보낼수 있음
```

```jsx
import App from "./App";
// index.js
```

### JSX

- 닫힘 규칙
  - `<div>`여는태그가 있으면, `</div>` 닫는 태그가 꼭 있어야 함
  - `<image />` `<br />` 이런식으로 꼭 셀프클로징 해주어야 함
- 최상위 태그 규칙

  - jsx로 컴포넌트 만들어서 return 하려면 반드시 최상위 태그로 다른 태그들을 묶어줘야 함
  - 만약 최상위 태그를 사용안한다면 React.Fragment로 감싸주기 or 그냥 빈 태그
    ```jsx
    import React from "react";
    ```
    ```jsx
    function App() {
      let name = "이름";

      return (
        <React.Fragment>
          <MyHeader />
          <header className="App-header">
            <h2>안녕 {name}</h2>
          </header>
          <MyFooter />
        </React.Fragment> // React.Fragment로 감싸주기
      );
    }
    ```
    ```jsx
    function App() {
      let name = "이름";

      return (
        <>
          <MyHeader />
          <header className="App-header">
            <h2>안녕 {name}</h2>
          </header>
          <MyFooter />
        </>
      );
    }
    // 빈태그
    ```

- 리액트 기능을 사용하지 않은 컴포넌트에서는 굳이 리액트 임포트 안해도된다
- jsx에서는 `class=`말고 `className=` 사용
- css파일을 만들지 않고 객체를 만들어서 인라인 스타일을 사용할 수 있다
  ```jsx
  // import "./App.css";
  import MyHeader from "./MyHeader";
  import MyFooter from "./Myfooter";
  function App() {
    let name = "hi";
    const style = {
      App: {
        backgroundColor: "black",
      },
      h2: {
        color: "red",
      },
      bold_text: {
        color: "green",
      },
    };
    return (
      <div style={style.App} className="App">
        <MyHeader />
        <h2 style={style.h2}>{name}</h2>
        <b style={style.bold_text} id="bold_text">
          react.js
        </b>
        <MyFooter />
      </div>
    );
  }

  export default App;
  ```
- jsx의 javascript 값 사용
  - 중괄호 안에 사용해야 함, jsx에서는 javascript의 변수나 값을 사용할 수 있음
  - 어떠한 함수의 호출이 되어도 되고, 문자열, 숫자 등 가능
  - 하지만 배열같은 것이 들어가면 포함이 되지 않는다. 숫자 문자열만 가능
- 조건부 렌더링
  ```jsx
  {
    number;
  }
  는: {
    number % 2 === 0 ? "짝수" : "홀수";
  }
  ```

### State(상태)

- State: 계속해서 변화하는 특정 상태, 상태에 따라 각각 다른 동작을 함
- ex. 다크모드와 라이트모드

```jsx
//App.js
import "./App.css";
import MyHeader from "./MyHeader";
import MyFooter from "./MyFooter";
import React from "react";
import Counter from "./Counter";

function App() {
  const number = 5;
  return (
    <div className="App">
      <MyHeader />
      <Counter />
      <MyFooter />
    </div>
  );
}

export default App;
```

```jsx
//Counter.js
import React, { useState } from "react";
// 상태를 사용하겠다
const Counter = () => {
  // 0: 동적으로 변해야 하는 값
  // 0에서 출발
  // 1씩 증가하고 1씩 감소하는
  // count 상태
  console.log("counter 호출!");
  const [count, setCount] = useState(0);
  // useState 는 배열을 반환하고 배열의 비구조 할당을 통해서
  // 0번째 인덱스 count, 1번째 인덱스 setCount
  // 라는 상수로 받아온걸 확인할 수 있음
  // setCount는 카운트라는 상태를 변화시키는 상태변화함수로 사용
  // 0은 초기값(0에서 출발)

  const onIncrease = () => {
    setCount(count + 1);
  };

  const onDecrease = () => {
    setCount(count - 1);
  };

  // state 2개 가져도 됨
  // 이름 달라야함
  const [count2, setCount2] = useState(0);
  const onIncrease2 = () => {
    setCount2(count2 + 1);
  };

  const onDecrease2 = () => {
    setCount2(count2 - 1);
  };
  return (
    <div>
      <h2>{count}</h2>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>

      <h2>{count2}</h2>
      <button onClick={onIncrease2}>+</button>
      <button onClick={onDecrease2}>-</button>
    </div>
  );
};
// onclick = 'onIncrease()' 이렇게 사용하는거 아님
export default Counter;

// 컴포넌트는 자신이 가진 state가 변화하면 화면을 다시 그려
// rerender를 한다
// 즉 함수가 다시 호출된다
```

### Props

- 컴포넌트에 데이터를 전달하는 방법

```jsx
// Counter.js
import React, { useState } from "react";

//props를 매개변수로 사용
const Counter = (props) => {
  console.log(props);
  const [count, setCount] = useState(props.initialValue);
  // 점 표기법 사용
  const onIncrease = () => {
    setCount(count + 1);
  };
  const onDecrease = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>
    </div>
  );
};

export default Counter;
```

```jsx
// App.js
import "./App.css";
import MyHeader from "./MyHeader";
import MyFooter from "./MyFooter";
import React from "react";
import Counter from "./Counter";

function App() {
  const number = 5;
  return (
    <div className="App">
      <MyHeader />
      <Counter a={1} initialValue={5} />
      <MyFooter />
    </div>
  );
}
export default App;
```

- `Counter initialValue={5}`: 자식컴포넌트에게 initialValue라는 이름을 붙여서 5라는 값을 전달해줄수있음
- 부모컴포넌트인 App 컴포넌트에서 자식인 Counter 컴포넌트에게 값을 이름에 붙여서 전달하는 방식을 props라고 부른다
- 몇개를 보내든 객체 안에 담겨서 오는걸 확인할 수 있음

---

- 아래처럼 코드 작성가능 **스프레드 연산자(spread operator) 사용**

```jsx
//App.js
import "./App.css";
import MyHeader from "./MyHeader";
import MyFooter from "./MyFooter";
import React from "react";
import Counter from "./Counter";

function App() {
  const number = 5;
  const counterProps = {
    a: 1,
    b: 2,
    c: 3,
    d: 4,
    e: 5,
    initialValue: 5,
  };
  return (
    <div className="App">
      <MyHeader />
      <Counter {...counterProps} />
      <MyFooter />
    </div>
  );
}

export default App;
```

```jsx
//Counter.js
import React, { useState } from "react";

//비구조화 할당을 통해서 받을수도 있음
const Counter = ({ initialValue }) => {
  const [count, setCount] = useState(initialValue);
  const onIncrease = () => {
    setCount(count + 1);
  };
  const onDecrease = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>
    </div>
  );
};

export default Counter;
```

---

- undefined

```jsx
import React, { useState } from "react";

const Counter = ({ initialValue }) => {
  const [count, setCount] = useState(initialValue);
  const onIncrease = () => {
    setCount(count + 1);
  };
  const onDecrease = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>
    </div>
  );
};
Counter.defaultProps = {
  initialValue: 0,
};
// undefined로 전달될것 같을때 defaultProps 설정
// 기본값을 설정하여 에러 방지
export default Counter;
```

---

- 짝수, 홀수 결과 기능 추가

```jsx
// OddEvenResult.js
const OddEvenResult = ({ count }) => {
  return <>{count % 2 === 0 ? "짝수" : "홀수"}</>;
};

export default OddEvenResult;
```

```jsx
// Counter.js
import React, { useState } from "react";
import OddEvenResult from "./OddEvenResult";

const Counter = ({ initialValue }) => {
  const [count, setCount] = useState(initialValue);

  const onIncrease = () => {
    setCount(count + 1);
  };
  const onDecrease = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={onIncrease}>+</button>
      <button onClick={onDecrease}>-</button>
      <OddEvenResult count={count} />
    </div>
  );
};
Counter.defaultProps = {
  initialValue: 0,
};

export default Counter;
```

- 리렌더 될때:
  1. 본인이 관리하고 본인이 가진 상태가 바뀔 때마다 리렌더가 된다
  2. 나에게 내려오는 props가 바뀔 때마다 리렌더가 된다
  3. 둘 다 아니어도 내 부모가 리렌더가 되면 나도 리렌더가 된다

---

props는 모두 다 전달할 수 있으며 컴포넌트 자체를 props로 전달할 수도 있다

```jsx
// App.js
import MyHeader from "./MyHeader";
import MyFooter from "./MyFooter";
import React from "react";
import Counter from "./Counter";
import Container from "./Container";
function App() {
  const number = 5;
  const counterProps = {
    a: 1,
    b: 2,
    c: 3,
    d: 4,
    e: 5,
  };
  return (
    <Container>
      <div>
        <MyHeader />
        <Counter {...counterProps} />
        <MyFooter />
      </div>
    </Container>
  );
}

export default App;
// App.js에서 Container 안에 자식요소로 div와 다른 컨테이너를 넣어줌
```

```jsx
// Container.js
const Container = ({ children }) => {
  return (
    <div style={{ margin: 20, padding: 20, border: "1px solid grey" }}>
      {children}
    </div>
  );
};

export default Container;
// Container 자식요소 children을 만들어서 컨테이너 안에 넣을 자식요소 {children}을 보여주도록 함
// react.element를 props로 받은 것
```

---

Image Reference:

[https://medium.com/@surksha8/virtual-dom-and-real-dom-understanding-the-differences-da8f3fab4261](https://medium.com/@surksha8/virtual-dom-and-real-dom-understanding-the-differences-da8f3fab4261)

## [Feelings+Finding]

- **State**는 컴포넌트 내부에서 관리되는 데이터이다. 그리고 State는 컴포넌트의 상태를 유지하며, 컴포넌트 내부에서 변경될 수 있다. State의 변화는 컴포넌트의 재렌더링을 유발할 수 있으며, React는 State가 변경될 때 컴포넌트의 UI를 업데이트 한다
- **Props**는 "properties"의 약자로, 컴포넌트에 전달되는 데이터이다. Props는 부모 컴포넌트로부터 자식 컴포넌트로 데이터를 전달할 때 사용된다

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
