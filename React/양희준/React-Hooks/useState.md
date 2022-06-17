# useState

## 📌 useState란?
- 상태를 관리하는 Hook이다.
- useState는 배열을 반환하기 때문에 구조 분해 할당으로 사용한다.
- 첫 번째 요소는 상태이며 두 번째 요소는 상태를 변화시키는 함수를 반환하고 있다.
- 상태가 변화하면 화면이 다시 랜던링 된다.
- setState 함수는 넣어줄 경우 비동기적으로 작동할 수 있다.

[React 공식문서](https://ko.reactjs.org/docs/faq-state.html#gatsby-focus-wrapper)

## 📌 useState 기본 형태

- const [상태, 상태 변환 함수] = useState("기본값")

```javascript
import React, { useState } from 'react';

function App() {
    // 보통 상태 변환 함수는 접두사 set을 붙혀서 의도를 정확하게 한다.
    const [num, setNum] = useState(0);
    // 상태를 변화시키는 이벤트
    const handleOnClick = () => setNum(num + 1);
    return (
        <div>
        {/* 현재 기본값은 0이다 */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```

## 📌 상태 변환 함수의 2가지 형태 (setState)

### 🧩 상태 변환 함수에 값을 넣어줄 경우

- 값을 넣어줄 경우 마지막으로 실행된 값으로 변경한다.
- 불필요한 랜더링을 막기 위해서 마지막 setState만 처리한다.

```javascript
import React, { useState } from 'react';

function App() {
    const [num, setNum] = useState(0);
    const handleOnClick = () => {
        // 예상 실행 0 + 1
        setNum(num + 1);
        // 예상 실행 1 + 2
        setNum(num + 2);
        // 예상 실행 3 + 3
        setNum(num + 3);
    }
    return (
        <div>
        {/* 결과 : 3 */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```

### 🧩 상태 변환 함수에 함수를 넣어줄 경우

- 연산의 결과를 다 처리해준다.
- 콜백함수의 인자는 바로 직전의 state 값이다.
- 콜백함수의 return 값이 state에 반영된다.

[React 공식 문서](https://ko.reactjs.org/docs/hooks-reference.html#usestate)

```javascript
import React, { useState } from 'react';

function App() {
    const [num, setNum] = useState(0);
    const handleOnClick = () => {
        // 예상 실행 0 + 1
        setNum((prevState) => prevState + 1);
        // 예상 실행 1 + 2
        setNum((prevState) => prevState + 2);
        // 예상 실행 3 + 3
        setNum((preState) => preState + 3);
    }
    return (
        <div>
        {/* 결과 : 6 */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```