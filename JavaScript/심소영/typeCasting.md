# 형변환

함수와 연산자에 전달되는 값을 적절한 자료형으로 변환시키는것.

자바스크립트의 형변환은 크게 두가지로 나뉜다.   
## 1. `암묵적 형변환(Implicit)또는 타입 강제 변환(Type coercion)`   
   - 표현식을 평가할때 문맥이 맞지 않는 상황에서 자바스크립트가 에러를 방지하기 위해 실행
  

## 2.  `명시적 형변환(Explicit)/또는 타입 캐스팅(Type casting)` 
 - 전달받은 값을 의도적으로 원하는 타입으로 변환


`암묵적 타입 변환은` 변수 값을 재할당해서 새로운 메모리 공간 확보를 하는 것이 아니라 자바스크립트 엔진이 표현식을 에러없이 평가하기 위해 기존 값을 바탕으로 새로운 타입의 값을 만들어 단 한번 사용하고 버린다.

`<형변환에 쓰이는 개념>`  
* `연산자` : 연산에 쓰이는 기호   
* `피연산자` : 연산에 참여하는 변수나 상수   
  ex) 3 + 5 (연산자: +, 피연산자: 3, 5)
#
## 1. 암묵적 형변환(Implicit)

[예시 코드] 문맥(context)상 맞지않는 상황
```js
// 표현식이 모두 문자열 타입이여야 하는 컨텍스트
'10' + 2               // '102'
`1 * 10 = ${ 1 * 10 }` // "1 * 10 = 10"

// 표현식이 모두 숫자 타입이여야 하는 컨텍스트
5 * '10' // 50

// 표현식이 불리언 타입이여야 하는 컨텍스트
!0 // true
if (1) { }
```

예시와 같은 상황에서 에러를 방지하기 위해 일어나는 현상.

### 1.1 문자열타입으로 변환
1. 문자열 연결 연산자의 역할은 문자열 값을 만드는 것이다.   
   따라서 문자열 연결 연산자의 피연산자는 문맥, 즉 컨텍스트 상 문자열 타입이여야 한다.   `> ES6에서 도입된 템플릿 리터럴의 문자열 인터폴레이션(String Interpolation)`   

[예시코드 1]

```js
// 숫자 타입
0 + ''              // "0"
-0 + ''             // "0"
1 + ''              // "1"
-1 + ''             // "-1"
NaN + ''            // "NaN"
Infinity + ''       // "Infinity"
-Infinity + ''      // "-Infinity"
// 불리언 타입
true + ''           // "true"
false + ''          // "false"
// null 타입
null + ''           // "null"
// undefined 타입
undefined + ''      // "undefined"
// 심볼 타입
(Symbol()) + ''     // TypeError: Cannot convert a Symbol value to a string
// 객체 타입
({}) + ''           // "[object Object]"
Math + ''           // "[object Math]"
[] + ''             // ""
[10, 20] + ''       // "10,20"
(function(){}) + '' // "function(){}"
Array + ''          // "function Array() { [native code] }"
```
### 1.2 숫자타입으로 암묵적 변환

1. 피연산자가 산술연산자를 만났을때 문맥상 피연산자는 숫자여야한다.
    
2. 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 NaN을 반환한다.
   
3. 빈 문자열(‘’), 빈 배열([]), null, false는 0으로, true는 1로 변환된다. 객체와 빈 배열이 아닌 배열, undefined는 변환되지 않아 NaN이 된다
 
[예시코드 1]  

```js
1 - '1'    // 0
1 * '10'   // 10
1 / 'one'  // NaN
```

[예시코드 2] 
```js
    '1' > 0   // true
```
[예시코드 3]
```js
    // 문자열 타입
    +''             // 0
    +'0'            // 0
    +'1'            // 1
    +'string'       // NaN
    // 불리언 타입
    +true           // 1
    +false          // 0
    // null 타입
    +null           // 0
    // undefined 타입
    +undefined      // NaN
    // 심볼 타입
    +Symbol()       // TypeError: Cannot convert a Symbol value to a number
    // 객체 타입
    +{}             // NaN
    +[]             // 0
    +[10, 20]       // NaN
    +(function(){}) // NaN
```

### 1.3 불리언 타입으로 암묵적 변환🎯

1. if 문이나 for 문과 같은 제어문의 조건식(conditional expression)은 불리언 값, 즉 논리적 참, 거짓을 반환해야 하는 표현식이다. 자바스크립트 엔진은 제어문의 조건식을 평가 결과를 불리언 타입으로 암묵적 타입 변환한다.
   
2. 불리언 타입이 아닌 값을 Truthy 값(참으로 인식할 값) 또는 Falsy 값(거짓으로 인식할 값)으로 구분한다. 즉, Truthy 값은 true로, Falsy 값은 false로 변환된다.

[예시코드 1]
```js
    if ('') console.log(x);
```
[예시코드 2]
```js
    if ('')    console.log('1');
    if (true)  console.log('2');
    if (0)     console.log('3');
    if ('str') console.log('4');
    if (null)  console.log('5');
    // 2 4
```
### 1.4 객체의 암묵적 형변환:dart:

자바스크립트에서 객체의 대부분의 암묵적 형변환은 `[object Object]`를 반환한다.   

모든 javascript의 객체는 toString메소드를 상속받을 수 있다.   

[예시코드]
  ```js
  const foo = {};
  foo.toString();
  // [object Object]
  ```

## 2. 명시적 형변환(Explicit)

개발자의 의도에 따라 코드 내에 타입을 변환한다.   
Object(), Number(), toString(), Boolean() 와 같은 함수를 이용하는데 new 연산자가 없다면 사용한 함수는 타입을 변환하는 함수로써 사용된다.

1. `래퍼 객체 생성자 함수를 new 연산자 없이 호출하는 방법` 
2. 자바스크립트에서 제공하는 `빌트인 메소드를 사용`  
3. 그리고 앞에서 살펴본 `암묵적 타입 변환을 이용하는 방법`이 있다.

### 2.1 문자열 타입으로 명시적 변환


2.1.1. String 생성자 함수를 new 연산자 없이 호출하는 방법   
   
[예시코드 1]
```js
  // String 생성자 함수를 new 연산자 없이 호출하는 방법
  // 숫자 타입 => 문자열 타입
  console.log(String(1));        // "1"
  console.log(String(NaN));      // "NaN"
  console.log(String(Infinity)); // "Infinity"
  // 불리언 타입 => 문자열 타입
  console.log(String(true));     // "true"
  console.log(String(false));    // "false"
```

2.1.2. Object.prototype.toString 메소드를 사용하는 방법   
   
[예시코드 2]
```js
// Object.prototype.toString 메소드를 사용하는 방법
// 숫자 타입 => 문자열 타입
console.log((1).toString());        // "1"
console.log((NaN).toString());      // "NaN"
console.log((Infinity).toString()); // "Infinity"
// 불리언 타입 => 문자열 타입
console.log((true).toString());     // "true"
console.log((false).toString());    // "false"

```
2.1.3. 문자열 연결 연산자를 이용하는 방법   

[예시코드 3]
```js
// 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
console.log(1 + '');        // "1"
console.log(NaN + '');      // "NaN"
console.log(Infinity + ''); // "Infinity"
// 불리언 타입 => 문자열 타입
console.log(true + '');     // "true"
console.log(false + '');    // "false"
```

`<명시적 문자열 변환시 주의할 개념>`   
 `>> ! 타입을 변환하는 함수에는 new연산자가 붙으면 안된다.`
* `new` : 생성자 함수의 연산자로, 생성자 함수 실행시 반드시 앞에 붙여준다.   
   클래스 타입의 인스턴스(객체)를 생성해주는 역할을 담당.   
new 연산자를 통해 메모리(Heap 영역)에 데이터를 저장할 공간을 할당받고   
    그 공간의 참조값(reference value /해시코드)을 객체에게 반환하여 주고 이어서 생성자를 호출한다.
* `생성자 함수` : 함수작성시 이름의 첫 글자는 대문자로 시작한다.
  반드시 'new' 연산자를 붙여 실행한다.

   
    
### 2.2 불리언 타입으로 명시적 변환
2.2.1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법   
[예시코드 1]
```js
// Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
console.log(Boolean('x'));       // true
console.log(Boolean(''));        // false
console.log(Boolean('false'));   // true
// 숫자 타입 => 불리언 타입
console.log(Boolean(0));         // false
console.log(Boolean(1));         // true
console.log(Boolean(NaN));       // false
console.log(Boolean(Infinity));  // true
// null 타입 => 불리언 타입
console.log(Boolean(null));      // false
// undefined 타입 => 불리언 타 입
console.log(Boolean(undefined)); // false
// 객체 타입 => 불리언 타입
console.log(Boolean({}));        // true
console.log(Boolean([]));        // true
```
2.2.2. ! 부정 논리 연산자를 두번 사용하는 방법   
[예시코드 2]   
```js
// 부정 논리 연산자를 두번 사용하는 방법
// 문자열 타입 => 불리언 타입
console.log(!!'x');       // true
console.log(!!'');        // false
console.log(!!'false');   // true
// 숫자 타입 => 불리언 타입
console.log(!!0);         // false
console.log(!!1);         // true
console.log(!!NaN);       // false
console.log(!!Infinity);  // true
// null 타입 => 불리언 타입
console.log(!!null);      // false
// undefined 타입 => 불리언 타입
console.log(!!undefined); // false
// 객체 타입 => 불리언 타입
console.log(!!{});        // true
console.log(!![]);        // true
```
### 2.3 단축평가

단축 평가는 아래와 같은 상황에서 유용하게 사용된다.   
1. 객체가 null인지 확인하고 프로퍼티를 참조할 때
   - 객체가 null인 경우, 객체의 프로퍼티를 참조하면 타입 에러(TypeError)가 발생 
2. 함수의 인수(argument)를 초기화할 때 
   - 함수를 호출할 때 인수를 전달하지 않으면 매개변수는 undefined를 갖는다. 이때 단축 평가를 사용하여 매개변수의 기본값을 설정하면 undefined로 인해 발생할 수 있는 에러를 방지할 수 있다.  

2.3.1. 논리곱 연산자 &&는 두개의 피연산자가 모두 true로 평가될 때 true를 반환한다. 
 ```js
   // 논리곱(&&) 연산자
'Cat' && 'Dog'  // Dog
false && 'Dog'  // false
'Cat' && false  // false
```
2.3.2. 논리합 연산자 ||는 두개의 피연산자 중 하나만 true로 평가되어도 true를 반환한다.
```js
   // 논리합(||) 연산자
'Cat' || 'Dog'  // 'Cat'
false || 'Dog'  // 'Dog'
'Cat' || false  // 'Cat'
```