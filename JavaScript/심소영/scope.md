# 1. 스코프
## 1.1 스코프(유효범위)의 정의
   * 변수의 수명을 의미.
   * 변수에 담긴 값을 찾을 때 확인하는 곳.
   * 변수가 정의된 위치에 의해서 결정된다.
   * `현재 실행되는 컨텍스트`를 말한다.   
    컨텍스트 :  값과 표현식이 "표현"되거나 참조 될 수 있음을 의미.   

   * 변수 또는 표현식이 "해당 스코프"내에 있지 않다면 사용할 수 없다. 
  
   * `계층구조`를 가지기 때문에 `하위 스코프는 상위 스코프에 접근` 가능. `반대는 불가`하다.

   * `전역변수` / `지역변수`

   * `정적유효범위` / `동적유효범위` 
  
#
## < 정적유효범위와 동적유효범위 >

## 1. 정적유효범위 (Static scope)

   * 선언된 변수는 선언된 블록 내에서만 유효함
   * 함수가 어디서 선언되었는지에 따라서 스코프가 결정된다
   * 자바스크립트의 정적 스코프는 전역 스코프, 블록 스코프, 함수 스코프에 적용된다

[예시코드 10]
```js
var num = 100;
function foo() {
  var num = 10;
  console.log(`foo : ${num}`);
  bar();
}
function bar() {
  console.log(`bar : ${num}`);
}
foo();
//foo : 10
//bar : 100
```

## 2. 동적 유효범위 (dynamic scope) 

   * 선언된 변수는 선언된 블록의 실행이 끝날 때까지 유효함❓
   * 실행 경로에 따라 유효범위가 달라질 수 있다. 
   * 프로그램의 런타임이나 실행 컨텍스트, 호출 컨텍스트에 의해 결정되는 스코프이다.

***
## < 전역스코프와 지역스코프 >   
## 1. 전역스코프 (global scope)
    
   * 전역 변수는 프로그램 전체에서 쓰이는 변수. 전역 스코프를 가지고있으며 전역 객체(window)의 프로퍼티.
   * 전역스코프의 변수는 전역에 선언되어있어 어느곳에서든 해당 변수에 접근 가능
   
   ### 전역변수
   * 전역변수를 사용하고 싶지 않을때는 익명함수 사용   
   * `암묵적 전역변수(implicit global)` : var 키워드를 생략한 변수는 암묵적으로 전역변수가 된다.   
   개발자가 의도하지 않은 암묵적 전역변수는 오류 발생의 원인이 된다.
   * `스트릭트 모드(strict mode)` : ES5 자바스크립트에서 사용하는 암묵적 전역 변수를 막기 위한 모드이다.   
    주로 코드 전체를 즉시실행 함수로 감싸는 기법을 사용하여 적용한다.❓   
    이유는 전역에 스트릭트 모드를 적용하면 내가 작성하지 않은 곳에서 에러가 발생할 수 있기 때문이다.

[예시코드 1]
```js
let a = 1; // 전역 스코프
function print() { // 지역(함수) 스코프
  let a = 111;
  console.log(a); // 111
}
print();
console.log(a); // 1
```
> 전역스코프와 지역스코프의 적용 범위

#
## 2. 지역스코프 (local scope)
   * 함수 스코프 (function-level scoped)
   * 함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다.
  ### 지역변수
   * 해당 지역에서만 접근할 수 있어 지역을 벗어난 곳에선 접근할 수 없다.
   * 자바스크립트는 `함수의 안에 선언된 변수만 지역변수`가 되고   
     `for문이나 if문 같은 곳에서 선언된 변수는 전역변수로 선언`된다.


### 1. 함수 스코프
   * 자바스크립트에서는 `함수를 선언할 때마다 새로운 스코프를 생성`하게 된다.
   * 함수는 자바스크립트에서 `클로저 역할`을 하기 때문에 스코프를 생성한다.
   * 함수 내에 정의된 변수는 외부 함수나 다른 함수 내에서는 접근 할 수 없다. 
     
 예를 들어 다음과 같은 상황은 유효하지 않다.

[예시코드 1]
```js
function exampleFunction() {
    var x = "declared inside function";
    // x는 오직 exampleFunction 내부에서만 사용 가능.
    console.log("Inside function");
    console.log(x);
}

console.log(x);  // 에러 발생 
// Uncaught ReferenceError: x is not defined
```

그러나 아래와 같은 코드는 변수가 함수 외부의 전역에서 선언되었기 때문에 유효하다. 
```js
var x = "declared outside function";

exampleFunction();

function exampleFunction() {
    console.log("Inside function");
    console.log(x);
}

console.log("Outside function");
console.log(x);
```
***
## < var 사용에 따른 차이 >

 * 함수 안에서 변수를 호출할 때 var를 사용하면 지역변수로 인식.  
   var를 사용하지 않으면 전역변수를 찾아 그 값을 가져온다.

[예시코드 1]
```js
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
<script type="text/javascript">
	var vscope = 'global'; //전역변수 vscope
	function fscope1(){
		var vscope = 'local'; //var로 지역변수 vscope를 선언하고 값을 넣는다.
	}
	fscope1(); //지역변수가 선언되고 값이 들어간다.
	alert(vscope); //전역변수를 바꾸지 않아 global 출력
	
	function fscope2(){
		vscope = 'local'; //전역변수 vscope 값 변경
	}
	fscope2(); //전역변수 값 변경
	alert(vscope); //local출력 //전역변수가 바뀌어 local 출력
	
</script>
</body>
</html>
```

[예시코드 - 함수 스코프, 블록스코프]
```js
function print() { // 함수 스코프
 console.log(a);
}
{ // 블록 스코프
 const a = '1';
}
```
***
## <익명함수> ❓
   * 익명함수를 사용하면 전역변수를 선언하지 않고 `모두 지역변수로 선언`할 수 있다.
   * 변수에 함수의 코드를 저장하는 대신 함수명을 사용하지 않는다.
   * 변수명을 마치 함수명처럼 사용해서 함수를 호출하거나 변수값을 이동시키는데 사용.
   * 코드 양이 많아졌을 때 변수들의 충돌을 예방해준다.

[예시코드 1]
```js
  //익명 함수 선언 및 변수에 대입
  var hello = function()
  {
    document.write("Hello World!");
  };

  //익명 함수 변수명으로 호출
  hello();
  // "Hello World!" 출력
```
[예시코드 2]
```js
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
<script type="text/javascript">
	//전역변수를 사용하고 싶지 않을 때 
(function(){
	var	MYAPP = {} 
	MYAPP.calculator = {
	    'left' : null,
	    'right' : null
	}
	MYAPP.coordinate = {
	    'left' : null,
	    'right' : null
	}
	 
	MYAPP.calculator.left = 10;
	MYAPP.calculator.right = 20;
	function sum(){
	    return MYAPP.calculator.left + MYAPP.calculator.right;
	}
	document.write(sum());
}())
//익명함수를 통해서 지역변수로만 사용하게 한다.
</script>
</body>
</html>
```
***
## 즉시실행함수

   * 한번의 실행만 필요로 하는 초기화 코드부분에 사용됨
   * 변수를 전역으로 선언하는것을 피하기 위해 사용

### 기본문법
```js
(function() {
 
})();
```
>함수에 ()를 씌워서 전역변수를 외부로부터 보호하고 그 뒤에 다시 ()를 붙여서 함수를 즉시 실행한다.

[예시코드]
```js
(function() {
  var color = 'blue';

  console.log('I like ' + color);

  setTimeout(function() {
    console.log('I like ' + color);
  }, 1000);
})();

var color = 'red';

console.log('I like ' + color);

setTimeout(function() {
    console.log('I like ' + color);
}, 1000);

// I like blue
// I like red
// I like blue
// I like red 출력
```
>변수 blue가 있는 부분이 즉시실행함수   
즉시실행함수안에 선언된 color는 함수 scope에 종속된 지역변수가 되기 때문에   
아래의 전역 변수 color의 영향을 받지 않고 'blue'라는 값을 유지하게 된다.

