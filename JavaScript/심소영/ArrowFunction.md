# 화살표 함수 (Arrow Function)

### 기본문법

**< 매개변수 지정 방법 >**   
```js
() => { ... } // 매개변수가 없을 경우
x => { ... } // 매개변수가 한 개인 경우, 소괄호를 생략할 수 있다.
(x, y) => { ... } // 매개변수가 여러 개인 경우, 소괄호를 생략할 수 없다.
```
**< 함수 몸체 지정 방법 >**   
```js
x => { return x * x }  // single line block
x => x * x             // 함수 몸체가 한줄의 구문이라면 중괄호를 생략할 수 있으며 
                       //암묵적으로 return된다. 위 표현과 동일하다.

() => { return { a: 1 }; }
() => ({ a: 1 })  // 위 표현과 동일하다. 객체 반환시 소괄호를 사용한다.

() => {           // multi line block.
const x = 10;
return x * x;
};
```
#

화살표 함수의 사용

- 함수 표현식과 같은 방법으로 사용할 수 있다.
- 함수를 동적으로 만들 수 있다.
  ```js
  let age = prompt("나이를 알려주세요.", 18);

  let welcome = (age< 18)?
    () => alert('안녕);
    () => alert('안녕하세요');

  welcome();
  ```
- 본문이 한 줄인 간단한 함수는 화살표 함수로 간편하게 만들 수 있다.


## 화살표 함수의 특징

### 1. 고유한 `this가 없다.`   
  따라서 화살표함수 본문에서 this에 접근하면 외부에서 값을 가져온다.
  아래 예시의 객체 메소드(showList()) 안에서 동일 객체의 프로퍼티(students)를 대상으로 순회하는데에 사용 할 수 있다.

  일반 함수와는 달리 화살표 함수의 this는 언제나 상위 스코프의 this를 가리킨다.(Lexical this라고 한다.)

[예시코드 -일반함수로 쓴 경우]
```js
//일반 함수로 쓸 경우
//콜백 함수의 this는 따로 call, aplt, bind 하지않는 한 전역객체를 가리킨다.

let group = {
    title: '1모둠'
    student: ['보라','호진','지민']

    showList() {
        this.students,forEach( // this === group
            function(student) { alert(this.title + ': ' + student) } // this === window
        );
    }
};

group.showList();

// undefined : 보라
// undefined : 호진
// undefined : 지민
```
[예시코드 - 화살표 함수로 쓴 경우]
```js
let group = {
    title: '1모둠'
    student: ['보라','호진','지민']
    
    showList() {
        this.students,forEach( // this === group
         student => alert(this.title + ': ' + student) // this === group
      );
    }
};

group.showList();

//1모둠 : 보라
//1모둠 : 호진
//1모둠 : 지민
```
> 예시의 forEach에서 화살표 함수를 사용했기에,   
> 화살표 함수 본문에 있는 this.title은 화살표 함수 바깥에 있는 메서드인 showList가 가리키는 대상과 동일해진다.   
> **`즉  this.title은 group.title과 같다.`**

### 2. 화살표 함수는 new와 함께 실행할 수 없다.

this가 없기 때문에 화살표 함수는 생성자 함수로 사용할 수 없다는 제약이 있다.   
화살표 함수는 new와 함께 호출할 수 없다.

### 3. 화살표 함수는 어떤 것도 바인딩 시키지 않는다.❓

화살표 함수 VS 바인드
화살표 함수와 일반 함수를 .bind(this)를 사용해 호출하는 것에는 ❓미묘한 차이❓가 있다.   
.bind(this)는 함수의 '한정된 버전(bound version)'을 만든다.❓  
화살표 함수엔 단지 this가 없을 뿐 어떤 것도 바인딩 시키지 않는다.❓❓   
화살표함수에서 this를 사용하면 일반 변수 서칭과 마찬가지로 this의 값을 외부 렉시컬 환경에서 찾는다.

### 4. 화살표 함수엔 arguments가 없다.
화살표 함수는 일반함수와 다르게 모든 인수에 접근할 수 있게 해주는 유사배열객체 arguments를 지원하지 않는다.

### 5. 화살표 함수는 super가 없다.

#
## 화살표 함수를 남용하면 안되는 경우

### 1. 메소드 정의 지양
```js
//bad

const person = {
    name: 'Lee',
    sayHi: () => console.log(`Hi ${this.name}`)
};
person.sayHi(); // Hi // undefined
```
> 메소드로 정의한 화살표 함수 내부의 this는 메소드를 호출한 객체를 가리키지 않고 상위 컨텍스트인 전역개체 window를 가리키게된다. 따라서 undefined가 출력되게 된다.

### 2. prototype 에 화살표함수로 정의된 메소드 할당 금지

화살표 함수로 정의된 메소드를 prototype에 할당하는 경우도   
화살표 함수로 객체의 메소드를 정의했을때와 동일한 문제가 발생한다.   
따라서 prototype에 메소드를 할당하는 경우, 일반 함수를 할당한다.
```js
// bad

const person = { // 모든 객체는 기본적으로 Object 객체에 프로토타입 체이닝 되어있다.
    name: 'Lee',
};

    Object.prototype.sayHi= () => console.log(`Hi ${this.name}`);

person.sayHi(); // Hi // undefined
```

### 3. new 생성자 함수로 사용 불가

생성자 함수는 prototype 프로퍼티를 가지며 prototype 프로퍼티가 가리키는 프로토타입 객체의 constructor를 사용한다.   
`화살표 함수는 prototype 프로퍼티를 가지고있지 않다.`   
따라서 화살표 함수는 생성자 함수로 사용할 수 없다.

```js
const Foo = (name) => {
    this.name = name
};

// 화살표 함수는 prototype 프로퍼티가 없다
console.log(Foo.hasOwnProperty('prototype'));// false

const foo = new Foo('FFF'); //TypeError: Foo is not a constructor
```

### 4. addEventListener 함수의 콜백함수로 쓰면 안된다.

addEventListener 함수의 콜백함수를 화살표 함수로 정의하면 this가 상위 컨택스트인 전역 객체 window를 가리키게 된다.

따라서 addEventListener 함수의 콜백함수 내에서 this를 사용하는 경우, function키워드의 일반 함수를 사용해야 한다.

일반 함수로 정의된 addEventListener 함수의 콜백함수 내부의 this는 이벤트 리스너에 바인딩된 요소(currentTarget)을 가리킨다.
```js
//bad
var button = document.getElementById('myButton');

button.addEventListener('click', () => {
    console.log(this === window); // =>true
    this.innerHTML = 'Clicked button';
});
```
```js
//Good
var button = document.gerElementById('myButton');

button.addEventListener('click', function() {
    console.log(this === button); // => true
    this.innerHTML = 'clicked button';
});
```
### 5. 화살표 함수는 call, apply, bind메소드를 사용해 this를 변경할 수 없다.
```js
window.x = 1;
const normal = function() { return this.x};
coonst arrow = () => this.x;

console.log(normal.call({x:10}))); // 10
console.log(arrow.call({x:10})); // 1
```