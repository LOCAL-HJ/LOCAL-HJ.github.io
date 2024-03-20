---
title: "[클라우딩 어플리케이션 엔지니어링] TIL_(2/5)"
excerpt: "프로그래머스 웹앱 엔지니어링 데브코스 2월 5일"

categories:
  - Programmers
tags:
  - [프로그래머스, 데브코스]

permalink: /programmers/programmers-til19

toc: true
toc_sticky: true

date: 2024-2-5
last_modified_at: 2024-2-5
---

## [Facts]

- React에서 사용자 입력 처리
- React에서 DOM 조작하기 - useRef
- React에서 배열 사용하기 - 리스트 렌더링(조회)

## [TIL]

### 다양한 사용자 입력 처리하기

- 한줄 입력 처리하기
- 여러줄 입력 처리하기
- 선택박스 입력 처리하기
- 사용자 입력 데이터 핸들링하기

```jsx
import { useState } from "react";

const DiaryEditor = () => {
  const [author, setAuthor] = useState("");
  return (
    <div className="DiaryEditor">
      <h2>오늘의 일기</h2>
      <div>
        <input
          name="author"
          value={author}
          onChange={(e) => {
            console.log(e.target.value);
            console.log(e.target.name);
            setAuthor(e.target.value);
          }}
        />
      </div>
    </div>
  );
};
export default DiaryEditor;
```

- onChange: 이벤트 , 값이 바뀌었을때 수행하는 이벤트
- onChange를 input에 등록하면 input이 변화할때 마다 콜백함수를 작동시킬 수 있음

---

```jsx
import { useState } from "react";

const DiaryEditor = () => {
  const [author, setAuthor] = useState("");
  const [content, setContent] = useState("");

  return (
    <div className="DiaryEditor">
      <h2>오늘의 일기</h2>
      <div>
        <input
          name="author"
          value={author}
          onChange={(e) => {
            setAuthor(e.target.value);
          }}
        />
        <textarea
          value={content}
          onChange={(e) => {
            setContent(e.target.value);
          }}
        />
      </div>
    </div>
  );
};
export default DiaryEditor;
// textarea(여러줄 입력)도 input처럼 작성해주면 된다
```

- 위 코드를 아래의 코드처럼 바꿀 수 있음 (state를 묶어줌)

```jsx
import { useState } from "react";

const DiaryEditor = () => {
  const [state, setState] = useState({
    author: "",
    content: "",
  });

  return (
    <div className="DiaryEditor">
      <h2>오늘의 일기</h2>
      <div>
        <input
          name="author"
          value={state.author}
          onChange={(e) => {
            setState({
              author: e.target.value,
              content: state.content,
            });
          }}
        />
        <textarea
          value={state.content}
          onChange={(e) => {
            setState({
              author: state.author,
              content: e.target.value,
            });
          }}
        />
      </div>
    </div>
  );
};
```

```jsx
// 스프레드 연산자 사용
// 원래있던 state를 작성해준 다음,
// 변경하고자 하는 state의 프로퍼티를 작성해준다
 <input
          name="author"
          value={state.author}
          onChange={(e) => {
            setState({
              ...state,
              author: e.target.value,
            });
          }}
        />
        <textarea
          value={state.content}
          onChange={(e) => {
            setState({
              ...state,
              content: e.target.value,
            });
          }}
        />
```

```jsx
// 상태변화 이벤트 핸들러도 합칠 수 있음
const handleChageState = (e) => {
  setState({
    ...state,
    [e.target.name]: e.target.value,
  });
};

return (
  <div className="DiaryEditor">
    <h2>오늘의 일기</h2>
    <div>
      <input name="author" value={state.author} onChange={handleChageState} />
      <textarea
        name="content"
        value={state.content}
        onChange={handleChageState}
      />
    </div>
  </div>
);
```

### React에서 DOM 조작하기 - useRef

- 일기 저장 버튼을 클릭했을때 작성자와 일기가 정상적으로 입력되었는지 확인하고 아니라면 focus하기
- `useRef.current`: 태그 자체를 뜻함

```jsx
const authorInput = useRef();
const contentInput = useRef();
```

```jsx
const handleSubmit = () => {
  if (state.author.length < 1) {
    authorInput.current.focus();
    return;
  }
  if (state.content.length < 5) {
    contentInput.current.focus();
    return;
  }
  alert("저장 성공");
};
```

```html
<input
  ref="{authorInput}"
  name="author"
  value="{state.author}"
  onChange="{handleChageState}"
/>
```

### React에서 배열 사용하기 - 리스트 렌더링(조회)

- 배열을 이용하여 React에서 List를 렌더링 하고 개별적인 컴포넌트로 만들기

```jsx
const DiaryList = ({ diaryList }) => {
  console.log(diaryList);
  return (
    <div className="DiaryList">
      <h2>일기 리스트</h2>
      <h4>{diaryList.length}개의 일기가 있습니다.</h4>
      <div>
        {diaryList.map(
          (
            it // it에는 diaryList배열의 하나하나의 요소가 it으로 바뀌어서 들어옴
          ) => (
            <div key={it.id}>
              <div>작성자 : {it.author}</div>
              <div>일기 : {it.content}</div>
              <div>감정 : {it.emotion}</div>
              <div>작성 시간(ms) : {it.created_date}</div>
            </div>
          )
        )}
      </div>
    </div>
  );
};

DiaryList.defaultProps = {
  diaryList: [],
};
// undefind 방지를 해결하기 위해
// defaultProps를 설정하여서 빈 배열 할당으로 해결

export default DiaryList;
// id를 이용하는 방법 말고 데이터에 고유한 id가 없다고 할 경우에는 index 사용
// 하지만 배열에 키로 인덱스를 사용할 경우 데이터를 삭제하거나 수정할때 인덱스 순서가 바뀌면 리액트에서 문제가 생길 수 있음
```

- 렌더링 된 아이템을 별도의 컴포넌트로 분리

```jsx
<div>
  {diaryList.map((it) => (
    <DiaryItem key={it.id} {...it} />
  ))}
</div>
```

```jsx
const DiaryItem = ({ author, content, created_date, emotion, id }) => {
  return (
    <div className="DiaryItem">
      <div className="info">
        <span>
          작성자 : {author} | 감정점수 : {emotion}{" "}
        </span>
        <br />
        <span className="date">{new Date(created_date).toLocaleString()}</span>
      </div>
      <div className="content">{content}</div>
    </div>
  );
};

export default DiaryItem;
```

## [Feelings+Finding]

- 스프레드 연산자는 배열이나 객체의 요소를 개별적으로 확장하는 데 사용되며 **`...`** 기호로 표현된다. 함수의 인자로 배열의 요소들을 개별적으로 전달하거나, 배열이나 객체를 복사하고 확장할 때 유용함
  ```jsx
  const fruits = ["apple", "banana"];
  const moreFruits = [...fruits, "orange", "grape"];

  console.log(moreFruits); // ['apple', 'banana', 'orange', 'grape']
  ```

---

    ⭐️ 개인 공부 기록용 블로그입니다 ⭐️
    오류나 틀린 부분이 있을 경우 메일로 지적해주시면 감사하겠습니다!😀
