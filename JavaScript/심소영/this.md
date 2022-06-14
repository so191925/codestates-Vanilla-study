# this

this의 값은 함수를 호출하는 방법에 의해 결정된다. (closure는 선언된 위치에 따라 달라짐)

자바스크립트에서 this는 객체를 가리키는 키워드다. 쉽게말해서 this는 객체이다.

대부분의 경우! this는 자신을 호출한 것 그자체를 말한다. this는 자신을 호출한 상위의 것이 없을 경우 기본값인 window객체가 된다.   
(window객체는 모든 객체를 가지고있으며 브라우저에 제공하는 전역객체다.)

생성자함수, 클래스문법에서 this에 할당한다는 것은 만들어진 자기자신(인스턴스)에 색상, 이름, 브랜드 등을 부여하겠다는 의미이다.

```js
let cat = {
    name: 'Tom',
    age: 3,
    printThis: function(){
        console.log(this); // cat 출력. this는 지금 cat임을 알수있다.
        console.log(this === cat); //true
        console.log(this.name); // Tom
        console.log(this.age); // 3
    }
};
cat.printThis(); //cat 객체의 내부함수인 printThis를 호출해주고 console.log를 출력해봄.

------------------------------------------------------------

let cat = {
    name: 'Tom',
    age: 3,
    printThis: function(){
        console.log(this); // window 출력. this는 지금 window객체임을 알수있다.
        console.log(this === cat); //false

   }
};

// 위 코드를 변수에 할당해보기
let printThis = cat.printThis;
printThis(); // 콘솔 각각 window, false가 출력된다. this가 달라졌기때문이다.


```

## 예외의 경우

1. 전역스코프에서 this는 window객체이다.
<!-- 2. 화살표함수에서는 this가 조금 달라진다. 
3. Strict Mode에서는 this가 조금 달라진다. --> 작성중


## bind : this를 원하는대로 설정할 수 있는 메서드 

ES5에서 정의해준 개념   
bind는 함수당 단 한번만 사용할 수 있다.

```js

function printThis(){
    console.log(this); // this가 뭔지 보기위해 찍어보는 콘솔로그, 디폴트값은 window
}
let cat1 = {
    name: 'Tom'
}
let cat2 = {
    name: 'Jerry'
}

let printThis1 = printThis.bind(cat1);
// bind메소드를 통해 printThis에 cat1을 바인딩해줬다.
// 그 결과로 printThis 의 this는 cat1이 되고 'Tom'이 출력된다.

// let printThis2 = printThis.bind(cat2); // bind는 한번만 적용되기때문에 this는 cat2와 상관없이 cat1이 되고 'Tom'이 출력된다.

```


