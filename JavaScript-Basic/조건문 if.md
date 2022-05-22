# 조건문

## 📌 조건문이란?

- 조건을 따라서 데이터를 처리를 다르게 하고 싶거나 결과값을 바꿀 때 사용한다.
- 조건에는 무조건 bool 즉 ture/false로 변환될 수 있는 값이 온다.

## 📌 조건문 if 문법

| 구문 | 의미 |
|:-----|:-----|
| if(조건 1) { 처리 1} | 조건 1이 true면 처리 1 실행 |
| else if(조건 2) { 처리 2 } | 조건 1이 false 조건 2 ture면 처리 2 실행 |
| else { 처리 3 } | 조건 1, 조건 2가 false이면 처리 3 실행 |

```javascript
const n = 2;
// 결과 : 짝수 입니다.
if (n === 0) {
    console.log("정수 입니다.");
} else if (n % 2 === 0) {
    console.log("짝수 입니다.");
} else console.log("홀수 입니다.");
```

## 📌 조건문 축약 표현

- 실행문이 하나이면 축약표현이 가능하다.

```javascript
const n = 1;
if (n === 1) console.log("숫자 1입니다.");
else console.log("숫자 1이 아닙니다.")
```

## 📌 조건문 특징

- 중첩이 가능하다.
- if - if else로 이어 나갈경우에 첫 번째 조건을 만나면 실행하고 조건문을 빠져나간다.

```javascript
// 중첩 가능
const n = 2;
if (n > 0) {
    if (n === 2) {
        console.log("숫자 2입니다.")
    }
}
```

```javascript
// 첫 번째 조건만 실행하고 반복문 탈출
const n = 2;
// 결과 : 자연수입니다.
if (n > 0) {
    console.log("자연수입니다.");
} else if (n % 2 === 0) {
    console.log("짝수입니다.");
}
```