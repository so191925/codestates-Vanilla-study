# 클로저

*클로저는 함수와 그 함수가 `선언됐을 때의 렉시컬 환경`(Lexical environment)과의 조합이다.*   
*클로저는 내부함수가 외부함수의 맥락(context)에 접근할 수 있는 것을 가리킨다*   
*클로저의 핵심은 스코프를 이용해서, 변수의 접근 범위를 닫는(폐쇄)것에 있다.*
*** 

예시 : 내부함수 인자값: y, 외부함수 인자값: x

**`내부함수는 외부함수 인자값 x에 접근할수있지만, 외부함수는 내부함수의 인자값 y에 접근할수없다.`**

이게 클로져함수의 특징이며, 반은 학교의 교칙을 따르지만 학교는 반 내부의 규칙을 따르지 않는다는 예시와 비슷하다.

* `클로져모듈`  
  수를 외부 `함수 스코프 안쪽에` 감추어, `변수가 함수 밖에서 노출되는 것을 막는 방법`

* `클로저의 단점`   
    클로저는 자신이 생성될 때의 환경(Lexical environment)을 기억해야 하므로 메모리 차원에서 손해를 볼 수 있다.   
    `일반 함수였다면 함수 실행 종료 후 가비지 컬렉션`(참고 자료: MDN '자바스크립트의 메모리 관리') 대상이 되었을 객체가, `클로저 패턴에서는 메모리 상에 남아` 있게 된다. 

    외부 함수 스코프가 내부 함수에 의해 언제든지 참조될 수 있기 때문이다. 따라서 클로저를 남발할 경우 퍼포먼스 저하가 발생할 수도 있다.

    자바스크립트는 가비지 컬렉션을 통해 메모리 관리를 한다. 객체가 참조 대상이 아닐 때, 가비지 컬렉션에 의해 자동으로 메모리 할당이 해제된다.

***

## < 렉시컬 환경이란 >
스코프는 함수를 호출할 때가 아니라 함수를 어디에 선언하였는지에 따라 결정된다. 이를 렉시컬 스코핑(Lexical scoping)라 한다.

[예시코드 1]
```js
function outerFunc() {
  var x = 10;
  var innerFunc = function () { console.log(x); };
  innerFunc();
}

outerFunc(); // 10
```
>함수 outerFunc 내에서 내부함수 innerFunc가 선언되고 호출되었다.   
이때 `내부함수 innerFunc는 자신을 포함하고 있는 외부함수 outerFunc의 변수 x에 접근할 수 있다.`   
이는 함수 innerFunc가 함수 outerFunc의 내부에 선언되었기 때문이다.  
함수 innerFunc는 함수 outerFunc의 내부에서 선언되었기 때문에 `함수 innerFunc의 상위 스코프는 함수 outerFunc`이다. 함수 innerFunc가 전역에 선언되었다면 함수 innerFunc의 상위 스코프는 전역 스코프가 된다.

***

## < 클로저의 활용 >

## 1. 현재 상태를 유지

`현재 상태를 기억하고 변경된 최신 상태를 유지하는 것`이 클로저가 가장 유용하게 사용되는 상황이다.   

현재 상태에 대한 정보를 유지해야 하는 경우
1. class처럼 사용하고 싶을 때
2. 정보의 은닉화

[예시코드]
```js
<!DOCTYPE html>
<html>
<body>
  <button class="toggle">toggle</button>
  <div class="box" style="width: 100px; height: 100px; background: red;"></div>

  <script>
    var box = document.querySelector('.box');
    var toggleBtn = document.querySelector('.toggle');

    var toggle = (function () {
      var isShow = false;

      // ① 클로저를 반환
      return function () {
        box.style.display = isShow ? 'block' : 'none';
        // ③ 상태 변경
        isShow = !isShow;
      };
    })();

    // ② 이벤트 프로퍼티에 클로저를 할당
    toggleBtn.onclick = toggle;
  </script>
</body>
</html>
```
#
## 2. 전역 변수의 사용 억제 ❓
[예시코드]
```js
<!DOCTYPE html>
<html>
  <body>
  <p>클로저를 사용한 Counting</p>
  <button id="inclease">+</button>
  <p id="count">0</p>
  <script>
    var incleaseBtn = document.getElementById('inclease');
    var count = document.getElementById('count');

    var increase = (function () {
      // 카운트 상태를 유지하기 위한 자유 변수
      var counter = 0;
      // 클로저를 반환
      return function () {
        return ++counter;
      };
    }());

    incleaseBtn.onclick = function () {
      count.innerHTML = increase();
    };
  </script>
</body>
</html>


let a = new hello('영서');
let b = new hello('아름');

a() //Hello, 영서
b() //Hello, 아름
```
> a와 b라는 클로저를 생성함으로써 함수 내부적으로 접근이 가능하다.

[예시코드 2]
```js
function a(){
  let temp = 'a' 
  
  return temp;
} 

// console.log(temp)  error: temp is not defined
const result = a()
console.log(result); //a
```
> 위 함수에 내부적으로 선언된 temp에는 직접적으로 접근을 할 수 없다.   
> 함수 a를 실행시켜 그 값을 result라는 변수에 담아 클로저를 생성함으로써 temp의 값에 접근이 가능하다.    
> 
이렇게 함수 안에 값을 숨기고 싶은 경우 클로저를 활용해볼 수 있다.

#
`변수의 값`은 누군가에 의해 `언제든지 변경될 수 있어 오류 발생의 근본적 원인`이 될 수 있다.   
상태 변경이나 가변(mutable) 데이터를 피하고 불변성(Immutability)을 지향하는 함수형 프로그래밍에서   
부수 효과(Side effect)를 최대한 억제하여 `오류를 피하고 프로그램의 안정성을 높이기 위해 클로저는 적극적으로 사용`된다.

[예시코드 - 함수형 프록래밍에서의 클로저 활용]❓

```js
// 함수를 인자로 전달받고 함수를 반환하는 고차 함수
// 이 함수가 반환하는 함수는 클로저로서 카운트 상태를 유지하기 위한 자유 변수 counter을 기억한다.
function makeCounter(predicate) {
  // 카운트 상태를 유지하기 위한 자유 변수
  var counter = 0;
  // 클로저를 반환
  return function () {
    counter = predicate(counter);
    return counter;
  };
}

// 보조 함수
function increase(n) {
  return ++n;
}

// 보조 함수
function decrease(n) {
  return --n;
}

// 함수로 함수를 생성한다.
// makeCounter 함수는 보조 함수를 인자로 전달받아 함수를 반환한다
const increaser = makeCounter(increase);
console.log(increaser()); // 1
console.log(increaser()); // 2

// increaser 함수와는 별개의 독립된 렉시컬 환경을 갖기 때문에 카운터 상태가 연동하지 않는다.
const decreaser = makeCounter(decrease);
console.log(decreaser()); // -1
console.log(decreaser()); // -2
```
>함수 makeCounter는 보조 함수를 인자로 전달받고 함수를 반환하는 고차 함수이다. 함수 makeCounter가 반환하는 함수는 자신이 생성됐을 때의 렉시컬 환경인 함수 makeCounter의 스코프에 속한 변수 counter을 기억하는 클로저다
