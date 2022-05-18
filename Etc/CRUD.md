# CRUD

- 가장 기본적인 데이터 처리 기능이다.
- Create, Read, Update, Delete의 앞 글자를 모아 만든 단어이다.

## CRUD 예시

- Create (생성)

```javascript
// 요소가 1,2,3,4인 배열 생성
const arr = [1,2,3,4];
```

- Read (읽기, 사용하는 방법)

```javascript
const arr = [1,2,3,4];
// 배열의 0번 인덱스를 읽기
console.log(arr[0]);
```

- Update (수정)

```javascript
const arr = [1,2,3,4];
// 배열의 1번 인덱스의 값을 1로 수정
arr[1] = 1;
```

- Delete (삭제)

```javascript
const arr = [1,2,3,4]
// 배열의 0번 인덱스의 값 삭제
arr.splice(0, 1);
```