# Ref

## 📌 Ref란?
- 리액트에서 DOM에 연결할 수 있는 방법을 제공한다.
- DOM을 꼭 사용해야하는 상황에 사용한다.

## 📌 Ref 사용방법

### 🧩 ref를 콜백함수로 호출하기

```javascript
import React, { Component } from 'react';

class App extends Component {
    // 버튼을 누르면 this.inputRef에 저장된 input의 DOM 정보를 보여준다
    // 결과 : <input>
    handleOnClick = () => console.log(this.inputRef);
    render() {
        return <div>
            {/* input의 요소를 this.inputRef에 연결 */}
            <input ref={(ref) => this.inputRef = ref} />
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

### 🧩 createRef 이용하기
current라는 객체에 정보가 담겨서 제공된다.

```javascript
import React, { Component, createRef } from 'react';

class App extends Component {
    // createRef로 ref 생성
    inputRef = createRef();
    // 버튼을 누르면 this.inputRef에 저장된 input의 DOM 정보를 보여준다
    // 결과 : { current : input }
    handleOnClick = () => console.log(this.inputRef);
    render() {
        return <div>
            {/* input의 요소를 this.inputRef에 연결 */}
            <input ref={this.inputRef} />
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

### 🧩 ref를 이용해서 focus 구현하기

```javascript
import React, { Component, createRef } from 'react';
// 버튼을 클릭하면 input에 focus를 해준다.
class App extends Component {
    inputRef = createRef();
    handleOnClick = () => this.inputRef.current.focus();
    render() {
        return <div>
            <input ref={this.inputRef}/>
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

## 📌 ref로 컴포넌트끼리 상호작용하는 방법
- 컴포넌트 자체에 ref를 걸게 되면 컴포넌트가 가지고 있는 props, 메소드, ref에 접근할 수 있다.
- **🔥 ref를 통해 컴포넌트끼리 상호작용하는 방법은 리액트의 설계방안과 어긋난 방법으로 Context API나 상태관리 라이브러리를 사용해야한다.**

```javascript
import React, { Component, createRef } from 'react';

class App extends Component {
    // createRef로 ref 생성
    inputBoxRef = createRef();
    // App에서 만든 버튼 핸들러 함수로 ref를 이용하여 자식 컴포넌트의 메소드를 사용할 수 있다.
    handleAppOnClick = () => this.inputBoxRef.current.handleOnClick();
    render() {
        return <React.Fragment>
            {/* 컴포넌트에 직접 App 컴포넌트에서 생성한 ref를 연결한다. */}
            <InputBox ref={this.inputBoxRef} />
            <button onClick={this.handleAppOnClick}>App</button>
        </React.Fragment>
    }
}
// 자식 컴포넌트
class InputBox extends Component {
    inputRef = createRef();
    handleOnClick = () => this.inputRef.current.focus();
    render() {
        return <div>
            <input ref={this.inputRef}/>
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

## ❓ 의문점

### 🧩 ref를 사용하지 않고 state에 input 값을 넣는 방법
```javascript
import React, { Component } from 'react';

class App extends Component {
    state = {
        text: ''
    }
    handleOnChange = (e) => this.setState({ text: e.target.value });
    handleOnClick = () => console.log(this.state.text);
    render() {
        return <div>
            <input onChange={this.handleOnChange}/>
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

### 🧩 ref를 사용해서 state에 input 값을 넣는 방법
```javascript
import React, { Component, createRef } from 'react';

class App extends Component {
    state = {
        text: ''
    }
    inputRef = createRef();
    handleOnClick = () => {
        this.setState({
            text: this.inputRef.current.value
        }, () => console.log(this.state.text));
    }
    render() {
        return <div>
            <input ref={this.inputRef}/>
            <button onClick={this.handleOnClick}>Click</button>
        </div>
    }
}

export default App;
```

- state를 계속 수정하는 현상은 render 함수를 계속 호출해서 재랜더링을 하는 과정이 과연 ref를 사용하는 동작보다 안좋은 현상인가?
- ref를 이용해서 마지막 값만 받는게 좋은현상으로 생각이 들지만 리액트는 가상돔을 사용하기 때문에 위 현상이 더 좋은건지 모르겠다.