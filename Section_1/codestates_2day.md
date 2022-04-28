# 코드스테이츠 - 2 day

## ✉️ 학습목표

> ### Chapter1. 조건문
> - truthy와 falsy 가 조건문에서 작동하는 방식을 이해할 수 있다.
> - 비교 연산자를 통한 엄격한 비교(=== , !==)에 대해 이해할 수 있다.
> - if 와 else if , else를 이해하고 무리 없이 활용할 수 있다.
> - 논리 연산자를 (&&, ||, ! ...) 통해 복잡한 조건을 간결하게 작성할 수 있다.
> - 복잡한 조건문을 활용하여, 실생활에서 쉽게 마주하는 문제를 해결하기 위한 알고리즘을 구현할 수 있다.

> ### Chapter2. 문자열
> - length 속성을 활용해 문자열의 길이를 확인할 수 있다.
> - 두 개 이상의 문자열을 하나의 문자열로 만들 수 있다.
> - slice() 메서드를 활용해 문자열을 원하는 만큼 ‘복사’할 수 있다.
> - 영문으로 된 문자열을 대문자 또는 소문자로 바꿀 수 있다.
> - 문자열 중 원하는 문자의 index를 찾고 접근할 수 있다 str.indexOf('a') 또는 str.lastIndexOf('a'),str[1]
> - includes() 메서드를 활용해 문자열 중 원하는 문자가 포함되어 있는지 알 수 있다. str.includes('a')
> - split() , join() 메서드를 활용해 문자열을 배열로 바꾸거나, 배열을 문자열로 바꿀 수 있다.
> - 템플릿 리터럴(Template literals) 문법을 사용할 수 있다.

## 조건문
질의어의 조건을 통해서 다른 결과나 실행을 하도록 컴퓨터에게 지시하는 문법

### 🧩 조건문 if문의 동작 과정
- if / else if / else 의 문법이 있으며 if와 else if 조건이 true가 만족하면 코드를 실행하고 빠져나간다.

```javascript
const age = 21;
// 결과 : 당신의 나이는 21살 입니다.
if (age === 21) {
    console.log("당신의 나이는 21살 입니다.");
} else if (age > 20) {
    console.log("당신의 나이는 20살 보다 많습니다.");
} else {
    console.log("당신의 나이는 20살 보다 적습니다.");
}
```

해당 코드에서 조건에 맞는 실행문은 if문과 else if문이 해당되지만 if와 else if문으로 조건문을 이어나가면 첫 번째 만난 조건이 true이면 조건문을 실행하고 해당 조건문을 빠져나가기 때문에 아래에 있는 조건문이 ture 값을 가져도 아래의 코드는 실행하지 않는다.

### 🧩 논리 부정 연산자
Boolean 값 앞에 `!`를 작성하면 값을 바꿔준다.

- true는 false로 바뀐다.
- false는 ture로 바뀐다.

```javascript
const notTrue = !true;
const notFalse = !false;
// 결과 : false
console.log(notTrue);
// 결과 : true
console.log(notFalse);
```

### 🧩 논리 연산자
논리 연산자를 통해서 복잡한 조건을 하나의 Boolean 값으로 나타내어 사용할 수 있다.

- && (And) : 모든 조건이 true이면 true이다. 하나의 조건이라도 false이면 false이다. 
- || (Or) : 모든 조건이 false이면 ture이다. 하나의 조건이라도 ture라면 true이다.

```javascript
const hour = 10;
const min = 30;
// 결과 : 해당 시간은 10시 30분 입니다.
if(hour === 10 && min === 30) {
    console.log("해당 시간은 10시 30분 입니다.");
}
// 결과 : 해당 시간은 10시에서 12시 사이입니다.
if(hour === 10 || hour === 11) {
    console.log("해당 시간은 10시에서 12시 사이입니다.")
}
```

```javascript
const hour = 11;
const min = 30;
//  출력 (x)
if(hour === 10 && min === 30) {
    console.log("해당 시간은 10시 30분 입니다.");
}
// 결과 : 해당 시간은 10시에서 12시 사이입니다.
if(hour === 10 || hour === 11) {
    console.log("해당 시간은 10시에서 12시 사이입니다.")
}
```

## 문자열
자바스크립트에서는 기본 자료형으로 문자들이 연결된 문자들의 집합이다.

### 🧩 연결 연산자 (+)
- 문자열과 문자열 사이에서 + 연산자를 사용하면 문자열을 연결한다.

```javascript
const head = "hello";
const tail = "world !!";
const result = head + " " + tail;
// 결과 : hello world !!
console.log(result);
```

`+` 연산자를 사용하면 문자열을 연결한다. 공백도 문자열이다.

### 🧩 문자열 메소드

### 문자열 추출
2개의 메소드 모두 시작점부터 끝점 -1 까지의 문자열을 정제한다. 원본 문자열은 바뀌지 않는다. 차이점은 음수 등등이 들어가면 작동 방식이 달라지지만 두개다 비슷한 기능을 수행한다.

- slice("시작점", "끝점")
- substring("시작점", "끝점")

### 문자열 검색
검색할 값과 시작 인덱스를 넣어주면 해당 문자열에서 검색을 시작한다 시작 인덱스를 넣어주지 않으면 0번 인덱스부터 수행한다. 또한 다른점은 indexOf는 인덱스 번호를 반환하며 요소가 없을 경우 -1를 반환하고 includes는 Boolean 값을 반환한다

- indexOf("검색할 값", "시작 인덱스")
- includes("검색할 값", "시작 인덱스")

### 문자열 정제
해당 문자열을 분리핧 대상 문자 기준으로 나눠주며 정지 카운터의 개수를 지정하면 앞에서 부터 해당 숫자만큼만 잘라주고 나머지는 그대로 반환한다.

- split('분리할 대상 문자', '정지 카운트')

- Math.ceil() : 올림
- Math.floor() : 내림
- Math.round() : 반올림
- Math.sqrt() : 제곱
- Math.abs() : 절대값
- Math.min() : 최소값
- Math.max() : 최대값

🏆  Pair : 조은영님