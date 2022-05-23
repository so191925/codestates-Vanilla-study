# 구조분해할당 (Destructuring)
### 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식
   * 구조 분해 할당이란 명칭은 `어떤 것을 복사`한 이후에 `변수로 '분해(destructurize)'`해준다는 의미
   * 이 과정에서 분해 대상은 `수정 또는 파괴되지 않는다.`
   * 함수에 객체나 배열의 `일부 데이터만 필요할 때 변수로 분해`
   * 함수의 매개변수가 많은 경우 
   * 함수의 매개변수 기본값이 필요한 경우 ❓

1. 배열 구조분해
2. 객체 구조분해
3. 중첩된 객체와 배열 구조분해
4. 함수 매개변수와 구조분해

## < 기본 문법 >

구조분해의 기본 문법은 아래와 같다.
```js
const [a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2 

const [c, d, ...rest] = [1, 2, 3, 4, 5, 6, 7];
console.log(c); // 1
console.log(d); // 2
console.log(rest); // [3, 4, 5, 6, 7]

const { e, f } = { e: 1, f: 2 };
console.log(e); // 1
console.log(f); // 2

const x = [1, 2, 3, 4, 5];
const [y, z] = x;
console.log(y); // 1
console.log(z); // 2
```

> 
객체 및 배열 리터럴 표현식을 사용하면 즉석에서 쉽게 데이터 뭉치를 만들 수 있다.
```js
var x = [1, 2, 3, 4, 5];
Copy to Clipboard
```
구조 분해 할당의 구문은 위와 비슷하지만, 대신 할당문의 좌변에서 사용하여, 원래 변수에서 어떤 값을 분해해 할당할지 정의한다.
```js
var x = [1, 2, 3, 4, 5];
var [y, z] = x;
console.log(y); // 1
console.log(z); // 2
```

****

## < 1. 배열 구조분해 >
   
   * 배열을 구조분해할당으로 분해시 인덱스로 접근하지 않고도 변수로 사용할 수 있게 된다.
#

### * 배열구조분해 변수 할당 기본 방법  
```js
var foo = ['one', 'two', 'three'];
var [one, two, three] = foo;

console.log(one); // "one"
console.log(two); // "two"
console.log(three); // "three"
```     
> foo에 one, two, three를 각각 저장한 후, 변수 one two three에 구조분해로 할당되어 출력
배열을 변수로 분해하는 과정    
# 
### * 배열에서 변수 재할당 
```js
const cafeMenu = ['iceLatte', 'iceDolceLatte']
```
>cafeMenu 배열에서 myPick이라는 변수에 iceLatte를,   
yourPick이라는 변수에 iceDolceLatte를 할당하고 싶을때

### 1.구조분해 할당 없이 변수명 재할당
```js
const myPick = cafeMenu[0];
const yourPick = cafeMenu[1];
```
>새로운 변수명에 cafeMenu 배열 안의 값을 대입해준다.   
구조 분해 할당 없이 재할당 가능

### 2.구조분해 할당을 이용해 변수명 재할당
```js
const [myPick,yourPick] = cafeMenu
console.log(myPick) // 'iceLatte'
console.log(yourPick) // 'iceDolceLatte'
console.log(cafeMenu) // ['iceLatte', 'iceDolceLatte']
```
#
### 1. '분해(destructuring)'는 '파괴(destructive)'를 의미하지 않는다.
구조 분해 할당이란 명칭은 어떤 것을 복사한 이후에 변수로 '분해(destructurize)'해준다는 의미 때문에 붙여졌다.   
이 과정에서 분해 대상은 수정 또는 파괴되지 않는다.

```js
// let [firstName, surname] = arr;
let firstName = arr[0];
let surname = arr[1];
```
> 배열의 요소를 직접 변수에 할당하는 것보다 코드 양이 줄어든다는 점만 다르다.
  
#
### 2. 쉼표를 사용하여 요소 무시하기
쉼표를 사용하면 필요하지 않은 배열 요소를 버릴 수 있다.
```js
// 두 번째 요소는 필요하지 않음
let [firstName, , title] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];

alert( title ); // Consul
```
>두 번째 요소는 생략되었지만, 세 번째 요소는 title이라는 변수에 할당된 것을 확인할 수 있다. 할당할 변수가 없기 때문에 네 번째 요소 역시 생략되었다.
#
### 3. 할당 연산자 우측엔 모든 이터러블이 올 수 있다.
배열뿐만 아니라 모든 이터러블(iterable, 반복 가능한 객체)에 구조 분해 할당을 적용할 수 있습니다.
```js
let [a, b, c] = "abc"; // ["a", "b", "c"]
let [one, two, three] = new Set([1, 2, 3]);
```
#
### 4. 할당 연산자 좌측엔 뭐든지 올 수 있다.
할당 연산자 좌측엔 ‘할당할 수 있는(assignables)’ 것이라면 어떤 것이든 올 수 있다.

아래와 같이 객체 프로퍼티도 가능하다.
```js
let user = {};
[user.name, user.surname] = "Bora Lee".split(' ');

alert(user.name); // Bora
```
#
### 5. .entries()로 반복하기 ❓
Object.entries(obj) 메서드와 구조 분해를 조합하면 객체의 키와 값을 순회해 변수로 분해 할당할 수 있다.
```js
let user = {
  name: "John",
  age: 30
};

// 객체의 키와 값 순회하기
for (let [key, value] of Object.entries(user)) {
  alert(`${key}:${value}`); // name:John, age:30이 차례대로 출력
}
```
#
### 6. 변수 교환 트릭
두 변수에 저장된 값을 교환할 때 구조 분해 할당을 사용할 수 있습니다.
```js
let guest = "Jane";
let admin = "Pete";

// 변수 guest엔 Pete, 변수 admin엔 Jane이 저장되도록 값을 교환함
[guest, admin] = [admin, guest];

alert(`${guest} ${admin}`); // Pete Jane(값 교환이 성공적으로 이뤄짐!)
```
>임시 배열을 만들어 두 변수를 담고, 요소 순서를 교체해 배열을 분해하는 방식을 사용했다.  
이 방식을 사용하면 두 개뿐만 아니라 그 이상의 변수에 담긴 값도 교환할 수 있다.
#

### 7. '…'로 나머지 요소 가져오기
배열 앞쪽에 위치한 값 몇 개만 필요하고 그 이후 이어지는 나머지 값들은 한데 모아서 저장하고 싶을 때는 점 세 개 ...를 붙인 매개변수 하나를 추가하면 ‘나머지(rest)’ 요소를 가져올 수 있다.
```js
let [name1, name2, ...rest] = ["Julius", "Caesar", "Consul", "of the Roman Republic"];

alert(name1); // Julius
alert(name2); // Caesar

// `rest`는 배열입니다.
alert(rest[0]); // Consul
alert(rest[1]); // of the Roman Republic
alert(rest.length); // 2
```
#
### 8. 기본값
할당하고자 하는 변수의 개수가 분해하고자 하는 배열의 길이보다 크더라도 에러가 발생하지 않는다. 할당할 값이 없으면 undefined로 취급되기 때문.
```js
let [firstName, surname] = [];

alert(firstName); // undefined
alert(surname); // undefined
```
> =을 이용하면 할당할 값이 없을 때 기본으로 할당해 줄 값인 '기본값(default value)'을 설정할 수 있다.
#



[예시코드 1]
```js
// 이름과 성을 요소로 가진 배열
let arr = ["Bora", "Lee"]

// 구조 분해 할당을 이용해
// firstName엔 arr[0]을
// surname엔 arr[1]을 할당하였습니다.
let [firstName, surname] = arr;

alert(firstName); // Bora
alert(surname);  // Lee
```
#
### [ split 같은 반환값이 배열인 메서드 사용 ]   
   * 사용법: `string.split( separator, limit )` >> (분할의 기준, 최대 분할 개수)   
   * limit 값을 정하지 않으면 전체를 다 분할한다.
  

[예시코드 split 1] 
```js
let arr = ["Bora", "Lee"]

let [firstName, surname] = "Bora Lee".split(' ');
```
>

[예시코드 split 2] 
```js
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="utf-8">
    <title>JavaScript</title>
  </head>
  <body>
    <p>abc,def,ghi</p>
    <script>
      var jbString = 'abc,def,ghi';
      var jbSplit = jbString.split(',');
      for ( var i in jbSplit ) {
        document.write( '<p>' + jbSplit[i] + '</p>' );❓
      }
    </script>
  </body>
</html>
```
![img](https://www.codingfactory.net/wp-content/uploads/JavaScript-split-01.png)
❓

***

## < 2. 객체 구조분해 >
   
   * 객체를 구조분해할당으로 분해시 

## 기본문법
```js
let {var1, var2} = {var1:…, var2:…}
```
>할당 연산자 `우측엔 분해하고자 하는 객체`를, `좌측엔 상응하는 객체 프로퍼티의 '패턴’`을 넣는다.


#
### 1. 기본 변수 할당
```js
var a = { p: 42, q: true };
var { p, q } = a;

console.log(p); // 42
console.log(q); // true
```
#
### 2. 선언에서 분리한 할당

```js
var a, b; ({a, b} = {a:1, b:2}); console.log(a); console.log(b);
```
#
### 3. 새로운 변수 이름에 할당
```js
var o = {p: 42, q: true};
var {p: foo, q: bar} = o;

console.log(foo); // 42
console.log(bar); // true  
```
>객체 구조분해를 사용하여 새로운 변수 이름에 값을 할당할 수 있다.
#

### 4. for...of문에서 구조분해 ❓
```js
var people = [
  {
    name: 'Mike Smith',
    family: {
      mother: 'Jane Smith',
      father: 'Harry Smith',
      sister: 'Samantha Smith',
    },
    age: 35,
  },
  {
    name: 'Tom Jones',
    family: {
      mother: 'Norah Jones',
      father: 'Richard Jones',
      brother: 'Howard Jones',
    },
    age: 25,
  },
];
for (var {
  name: n,
  family: { father: f },
} of people) {
  console.log('Name: ' + n + ', Father: ' + f);
}
// "Name: Mike Smith, Father: Harry Smith" 
// "Name: Tom Jones, Father: Richard Jones"
```
#
## < 객체에서 변수 재할당 >
```js
const basket = {
  shineMusket : 12000,
  tangerine: 8000
}
```
>basket 객체 안의 tangerine이라는 property를 grapeFruit으로 재할당을 원할때

### 1.구조분해 할당 없이 변수명 재할당
```js
const grapeFruit = basket.tangerine
```
>새로운 변수명에 basket의 tangerine과 같은 값을 대입해준다.
구조 분해 할당 없이 재할당 가능

### 2.구조분해 할당을 이용해 변수명 재할당
```js
const { tangerine: grapeFruit } = basket

console.log(grapeFruit) //8000
console.log(basket) // let basket = { shineMusket : 12000, tangerine: 8000}
```
>basket이라는 원본 객체의 값은 변하지 않지만, grapeFruit 변수에 basket.tangerine과 동일한 값을 적용

#
## < 3. 중첩된 객체와 배열 구조분해 > ❓

객체나 배열이 다른 객체나 배열을 포함하는 경우, 좀 더 복잡한 패턴을 사용하면 중첩 배열이나 객체의 정보를 추출할 수 있다. 이를 중첩 구조 분해(nested destructuring)라고 부른다.

```js
let options = {
  size: {
    width: 100,
    height: 200
  },
  items: ["Cake", "Donut"],
  extra: true
};

// 코드를 여러 줄에 걸쳐 작성해 의도하는 바를 명확히 드러냄
let {
  size: { // size는 여기,
    width,
    height
  },
  items: [item1, item2], // items는 여기에 할당함
  title = "Menu" // 분해하려는 객체에 title 프로퍼티가 없으므로 기본값을 사용함
} = options;

alert(title);  // Menu
alert(width);  // 100
alert(height); // 200
alert(item1);  // Cake
alert(item2);  // Donut
```
> `[해설]`   
> 예시에서 객체 options의 size 프로퍼티 값은 또 다른 객체이다.    
> items 프로퍼티는 배열을 값으로 가지고 있다.   
>  대입 연산자 좌측의 패턴은 정보를 추출하려는 객체 options와 같은 구조를 갖추고 있다.   
> 
> extra(할당 연산자 좌측의 패턴에는 없음)를 제외한 options 객체의 모든 프로퍼티가 상응하는 변수에 할당되었다.
> 
> 변수 width, height, item1, item2엔 원하는 값이, title엔 기본값이 저장되었다.   
> 위 예시에서 size와 items 전용 변수는 없다는 점에 유의.   
> 전용 변수 대신 size와 items 안의 정보를 변수에 할당하였다.


#
## < 4. 함수 매개변수와 구조분해 >

- 함수에 매개변수가 많은데 이중 상당수가 선택적으로 쓰이는 경우
- 넘겨주는 인수의 순서가 틀리면 문제가 생김

- 따라서 구조분해를 통해 함수를 리팩토링. --> 매개변수 모두를 객체에 모아 함수에 전달해, 함수가 전달받은 객체를 분해하여 변수에 할당하고 원하는 작업을 수행할 수 있도록 한다.

[예시코드 - 리팩토링 전]
```js
function showMenu(title = "Untitled", width = 200, height = 100, items = []) {
  // ...
}
```
>이렇게 함수를 작성하면 넘겨주는 인수의 순서가 틀려 문제가 발생할 수 있다.

[예시코드 - 리팩토링 전 2]
```js
// 기본값을 사용해도 괜찮은 경우 아래와 같이 undefined를 여러 개 넘겨줘야 합니다.
showMenu("My Menu", undefined, undefined, ["Item1", "Item2"])
```
>매개변수가 많아질수록 가독성이 떨어진다.
   

### 따라서 구조분해를 통해 매개변수를 전부 모아 함수에 전달 > 함수가 객체를 분해 > 변수에 할당하게 리팩토링을 한다.   

[리팩토링]
```js
// 함수에 전달할 객체
let options = {
  title: "My menu",
  items: ["Item1", "Item2"]
};

// 똑똑한 함수는 전달받은 객체를 분해해 변수에 즉시 할당함
function showMenu({title = "Untitled", width = 200, height = 100, items = []}) {
  // title, items – 객체 options에서 가져옴
  // width, height – 기본값
  alert( `${title} ${width} ${height}` ); // My Menu 200 100
  alert( items ); // Item1, Item2
}

showMenu(options);
```

[중첩 객체와 콜론을 조합한 구조분해]
```js
let options = {
  title: "My menu",
  items: ["Item1", "Item2"]
};

function showMenu({
  title = "Untitled",
  width: w = 100,  // width는 w에,
  height: h = 200, // height는 h에,
  items: [item1, item2] // items의 첫 번째 요소는 item1에, 두 번째 요소는 item2에 할당함
}) {
  alert( `${title} ${w} ${h}` ); // My Menu 100 200
  alert( item1 ); // Item1
  alert( item2 ); // Item2
}

showMenu(options);
```