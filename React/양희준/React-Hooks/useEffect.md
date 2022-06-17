# useEffect

## 📌 useEffect란?
- 컴포넌트가 랜더링 될 때마다 특정 작업을 수행하도록 할 수 있는 Hook이다.
- componentDidMount와 componentDidUpdate를 합친 형태이며 return 값으로 함수를 넘겨주면 componentDidUnMount로 작동한다.
- useEffect의 인자는 2개로 첫 번째 인자는 콜백함수를 받으며 두 번째 인자는 배열을 입력받는다.

## 📌 콜백함수만 인자로 사용할 때
랜더링이 되면 useEffect 함수 실행

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    // 처음 화면에 마운트 되었을 때 실행되고 그 이후에는 화면이 재랜더링 되면 함수 실행
    useEffect(() => {
        /*
        결과 : render
        그 다음 버튼을 누르면 계속 결과는 render이다.
        */
        console.log("render");
    });
    // 재랜더링을 위한 이벤트 핸들러 생성
    const handleOnClick = () => setIsChecked(!isChecked);
    // 버튼을 누르면 화면 재랜더링
    return <button onClick={handleOnClick}>Click</button>
}

export default App;
```

## 📌 콜백함수와 배열 모두 인자로 사용할 때
- 빈 배열을 인자로 줄 경우 화면이 최초로 랜더링 되었을 때만 호출된다.
- 배열의 인자에 state를 넣어줄 경우 해당 state의 상태가 변할 경우만 함수가 호출된다.

### 🧩 빈 배열을 인자로 사용할 때

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    // 두 번째 인자로 빈 배열을 입력
    useEffect(() => {
        // 첫 랜더링인 경우에만 실행
        console.log("render");
    }, []);
    const handleOnClick = () => setIsChecked(!isChecked);
    // 버튼을 클릭해도 콘솔창에 render가 호출되지 않음
    return <button onClick={handleOnClick}>Click</button>
}

export default App;
```

### 🧩 배열에 state을 넣어줄 때

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    const [num, setNum] = useState(0);
    // 두 번째 인자의 값에 state인 num을 입력
    useEffect(() => {
        // 첫 랜더링인 경우와 num이 변경될 때만 실행
        console.log("render");
    }, [num]);
    // num + 1을 해주는 이벤트 핸들러
    const updateNum = () => setNum(num + 1);
    // isChecked를 변경해주는 이벤트 핸들러
    const updateIsChecked = () => setIsChecked(!isChecked);
    
    return <div>
        <div>
            <span>{num}</span>
            <button onClick={updateNum}>numUpdate</button>
        </div>
        <button onClick={updateIsChecked}>isCheckedUpdate</button>
    </div>
}

export default App;
```

## 📌 함수를 return 값에 넣었을 때

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    const updateIsChecked = () => setIsChecked(!isChecked);
    return <div>
        {/* isChecked에 컴포넌트를 랜더링 */}
        {isChecked ? null : <Log/>}
        <button onClick={updateIsChecked}>isCheckedUpdate</button>
    </div>
}

const Log = () => {
    // 컴포넌트를 사용하지 않을 경우 return 값으로 반환하는 함수 실행
    useEffect(() => {
        return () => {
            // 컴포넌트가 언마운트 될 때마다 실행
            console.log("Log");
        }
    })
    return <span>Log</span>
}

export default App;
```