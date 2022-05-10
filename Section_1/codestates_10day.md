# 코드스테이츠 - 10 day

## ✉️ 학습목표

> ### Chapter1. 배열
> - 배열에서 특정 인덱스(index)의 요소(element)를 조회하거나, 변경할 수 있다.
> - length 속성을 이용하여 배열의 길이를 조회할 수 있다.
> - 배열의 요소가 배열인 이중 배열을 이해하고, 이중 배열의 요소를 조회하거나 변경할 수 있다.
> - 배열의 각 요소에 대하여, 반복하는 코드를 실행시킬 수 있다.
> - 배열에서 사용되는 다양한 메서드를 알고 사용할 수 있다.
> - split(), join(), slice(), splice(), Array.isArray(), push(), unshift(), pop(), shift(), indexOf(), includes()

## 배열 조회 (Read, Update)

- Read : 배열의 요소를 조회하는 행위
```javascript
const arr = [1,2,3,4];
// 배열 arr의 0번째 요소를 조회한다.
console.log(arr[0]);
```

- Update : 배열의 요소를 변경하는 행위
```javascript
const arr = [1,2,3,4];
// 배열 arr의 0번째 요소를 10으로 변경한다.
arr[0] = 10;
// 배열 arr를 조회한다.
console.log(arr);
```

## 배열의 길이를 조회하는 방법
프로퍼티 length를 사용하며 배열의 총 요소의 개수의 정보를 갖고 있다.

- Syntax : (조회하고싶은 배열).length

```javascript
const arr = [1,2,3,4,5];
// 결과 : 5 출력
console.log(arr.length);
// 결과 : 4 출력
console.log([1,2,3,4].length);
```

## 2차원 배열 선언과 조회하는 방법
2차원 배열을 선언하는 방법은 배열안에 요소를 배열로 전달한다.

```javascript
// 2차원 배열 선언
const arr = [[1,2], [3,4], [5,6]];
// arr의 0번째 요소인 [1,2] 값에서 0번째 요소를 조회 결과 : 1
console.log(arr[0][0]);
// arr의 1번째 요소인 [3,4] 값에서 0번째 요소를 조회 결과 : 3
console.log(arr[1][0]);
```

## 배열의 요소를 순회 하는 방법

### 1차원 배열

```javascript
const arr = [1,2,3,4];
// 0 ~ arr.length - 1 까지 반복문을 실행
for(let i = 0; i < arr.length; i++) {
    // i에 해당되는 요소 조회
    console.log(arr[i]);
}
```

배열의 길이는 4이지만 배열의 마지막 인덱스번호는 3이다. 왜냐하면 배열의 시작점은 0번째 요소부터 시작한다.

### 2차원 배열

```javascript
const arr = [[1,2], [3,4]];
// 0 ~ arr.length - 1 까지 반복문 실행
for(let i = 0; i < arr.length; i++) {
    // 0부터 arr의 요소가 배열이므로 그 배열의 길이 - 1 까지 반복문을 실행한다.
    for(let j = 0; j < arr[i].length; j++) {
        // arr[i]번째 요소인 배열의 j번째 요소를 조회
        console.log(arr[i][j]);
    }
}
```

> - split(), join(), slice(), splice(), Array.isArray(), push(), unshift(), pop(), shift(), indexOf(), includes()

## 배열의 타입 확인
정적 메소드 isArray를 사용한다.

- Syntax : Array.isArray(조회하고 싶은 변수나 값)
- 사용 목적 : typeof 연산자로 배열의 타입을 확인하면 "object"를 반환하기 때문이다.

```javascript
const arr = [1,2,3];
// 결과 : "object"
console.log(typeof arr);
```

```javascript
const arr = [1,2,3];
const str = "string";
// 결과 : true
console.log(Array.isArray(arr));
// 결과 : false
console.log(Array.isArray(str));
// 결과 : false
console.log(Array.isArray(3));
```

## Array.prototype.push
## Array.prototype.pop
## Array.prototype.unshift
## Array.prototype.shift
## Array.prototype.slice
## Array.prototype.splice
## Array.prototype.indexOf
## Array.prototype.includes
## Array.prototype.join