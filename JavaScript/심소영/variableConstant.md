# 변수와 상수

## 1. 변수  
   * 값이 담긴 공간
   * 값을 지니고있으며 `언제든 변경 가능, 사용 가능`
   * `var, let` 구문으로 선언 및 할당

## 2. 상수
   * 초기값 할당(초기화) 후 `변경 불가`
   * `const` 로 선언

## - 리터럴
   * 할당된 값 
   * ex) a = 'cat' // 'cat'이 string타입의 리터럴
   * 고정된 값 자체

초기값 할당이 없을시 묵시적으로 undefined를 가진다.

#
## <변수 Variable>
   
   * var, let 사용
  
   * `let사용 권장`(ES6부터 도입), var 지양

   * 초기값 할당이 없을시 undifined를 반환   
  
  [예시코드 1]
  ```js
  let box;
  console.log(box); //undefined
  ```

   * 콤마 (,) 를 사용시 여러개의 변수를 한번에 선언 가능      

[예시코드 2]
```js
let num1 = [1,2,3], num2 = 2, num3 ='3', num4 ;
// 변수 4개를 선언,초기화함
// 각각 배열Array, Number, string 타입
// num4는 초기값이 할당되지않아 undefined
 ```

## 1. let 
const구문은 재할당이 불가능하므로 에러발생
   * ES6에서 추가된 변수 선언 방식
   * let은 { } (block)단위의 scope를 가진다.
   * var와 차이점 : `같은 변수명을 두번 선언하면 오류가 남` 
   * 즉 변수의 `값을 재할당 해주는 방식`으로 사용.

[예시코드 1]
```js
let str='hello';  
{
  let str='world';  
  console.log(str); //world
}
console.log(str); //hello
```
> { } 불록 단위의 scope로 동작하기때문에 위와같은 결과가 나온다. 전역변수/지역변수 개념

## 2. var

   * ES6 이전에 나온 변수 선언방식. 사용지양
   * let과의 차이점 : scope개념. `function단위의 scope`를 가진다.
   * `같은 이름의 변수를 여러번 선언해도 오류가 나지 않는다.` 값이 바뀌기만 함

[예시코드 1]
```js
var str = "hello";
if(true){
	var str2="world";
}

console.log(str2);		//world
```
> if문 안에서 str2를 선언했지만 if문 밖에서도 변수가 유효하다.   
> console.log를 { } 블록 밖에서 찍었는데도 str2의 값이 출력된다.  
> var를 사용했기때문.

[예시코드 2]
```js
var str="hello";
var str="world";
console.log(str);	//world
```
>같은 이름의 변수를 두 번 선언해도 오류가 안남. 값만 바뀜
#
## !! var의 문제점 !!

### 1. 정의된 변수가 함수 스코프를 가진다.
   
[예시코드 1]
```js
function example() {

  var i = 1;  //함수 내부에서 변수 정의
}

console.log( i );  // 에러 발생 //함수바깥에서 사용
```
>var 키워드로 정의된 변수는 함수 스코프이기 때문에 `함수를 벗어난 영역에서 사용하면 에러`가 발생한다.

***
### 2. var 변수를 함수 안이 아닌 프로그램의 가장 바깥에 정의하면 전역변수가 된다. 🎯  
   
[예시코드 1]
```js
function example1() {
  i = 1;
}

function example2() {
  console.log( i );
}

example1(); // example1에서 넣었던 값이
example2(); // 1 //example2에서 출력된다.
```
> 함수안에서 var 키워드를 사용하지 않고 변수에 값을 할당하면 전역 변수가 된다. 🎯   
>
* 파일의 최상단에 `'use strict';`를 선언하면 이런경우가 전역변수가 되는것을 방지할 수 있다.   
 아래가 예시.

[예시코드 'use strict']
```js
'use strict';

function example1() {
  i = 1;  // 에러 발생 
  // VM10:4 Uncaught ReferenceError: i is not defined //정의되지 않았음
}

function example2() {
  console.log( i );
}

example1();
example2();
```
***
### 3. 반복문에서 정의된 변수가 반복문이 끝난 뒤에도 계속 남아있다. 
   * for, while, switch, if문 등 함수 내부에서 작동되는 모든 코드가 소멸되지 않고 계속 남아있는 문제가 있다.
  
[예시코드 1]
```js
for (var i = 0; i < 10; i++) {
  console.log(i); // 0...생략
}

console.log('last:', i);

// 0
// 1
// 2
// 3
// 4
// 5
// 6
// 7
// 8
// 9
// last: 10
```
> 위와 같이 for문이 끝난 이후에도 for문 안에 선언했던 i변수 값을 읽을 수 있다.   
> 
>` var 변수의 스코프를 제한하기 위해 즉시 실행 함수를 사용하기도 한다.`   
>즉시 실행 함수는 함수를 선언하는 시점에 바로 실행하고 사라지는 함수다.   
>var변수는 함수 스코프를 따르므로 즉시 실행 함수로 묶으면 변수의 스코프를 제한할 수 있다.

[예시코드 - 즉시실행함수]
```js
(function () {
  for (var i = 0; i < 10; i++) {
    console.log(i);
  }
})();

console.log('last:', i); // 에러 발생
```
***
### 4. 호이스팅 (hoisting)이 일어난다.

   * 호이스팅이란 var키워드로 정의된 변수가 그 변수가 속한 스코프의 최상단으로 끌어올려지는 것을 말한다.
   * `변수를 선언하기 전에 사용해도 에러가 발생되지 않는다.`   
   * 변수가 선언된 곳 위에서 값을 할당 할 수도 있다.
  
[예시코드 1]
```js
console.log(myVar);
var myVar = 1;
//에러가 일어나지 않는다.
//아래의 코드와 같이 변경됐다고 생각하면 됨.

var myVar = undefined;
console.log(myVar);
myVar = 1;
```
  >var로 선언한 변수는 `호이스팅 된 후에 undefined가 할당이 된다.`   
   실제 값은 원래 정의했던 그 위치에서 할당이 되는 것이다.

[예시코드 2]
```js
console.log( myVar ); //1을 출력
myVar = 2;
console.log( myVar ); //2를 출력
var myVar = 1;
```
> 에러없이 출력된다. 직관적이지 않으며 보통의 프로그래밍 언어에서는 찾아보기 힘들다.

### 5. var를 사용하면 한번 선언된 변수를 재선언 할 수 있다.
[예시코드 1]
```js
var myVar = 1;
var myVar = 2;
```
***
### 6. 어떤 값도 재할당 가능한 변수로 밖에 만들 수 없다.
   * 상수로 쓰여야 할 값도 무조건 재할당 가능한 변수가 된다.

[예시코드 1]
```js
var PI = 3.141592;
PI = 123;

//pi는 원주율로 상수여야하나 var사용시 재할당이 가능한 변수가 된다.
```

#

## <상수 Constant>
   * 고정값이라는 의미
   * `const`로 선언, 할당 (ES6부터 도입됨)
   * `{ } (block) scope`를 가진다. = let과 같은 스코프
   * 초기값 할당만 가능, `변경 불가`
   * const로 선언 후 변경이 필요할 시 let으로 변경 추천   

[예시코드 1]
```js
const num1 = 1;
num1 = 2;
//Uncaught TypeError: Assignment to constant variable.
```
> const구문은 재할당이 불가능하므로 에러발생