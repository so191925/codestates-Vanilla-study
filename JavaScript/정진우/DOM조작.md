# DOM 조작

## 📌 1. Element 생성하기

`document.creatElement()` 메서드를 이용해 새로운 요소를 만들 수 있습니다. 이렇게 만들어진 요소는 DOM에 추가하는 메서드를 사용해 추가하기 전까지는 DOM에 추가되지 않고 메모리에만 존재합니다.

```javascript
const tweetDiv = document.createElement("div");
```

코드를 작성하고 html코드를 봐도 div가 추가된 흔적이 없다. `tweetDiv` 라는 요소는 현재 공중부양 상태이다. 아무것도 연결이 되어있지 않은 하나의 노드가 방금 생성한 `tweetDiv` 이다.
![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/zzQEJU2F0-1597040532407.gif)

## 📌 2. Element 추가

공중에 떠있는 엘리먼트를 `append`해서 실제 웹페이지 상에 보여진다.  
div 요소에 아무런 내용을 입력하지 않아서 보이는 내용이 없지만 div요소가 생성된것을 볼 수 있다.

```javascript
document.body.append(tweetDiv);
```

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/80LDLyQyZ-1597040631488.gif)

## 🧩 append vs appendChild 차이

append와 appendChild 메서드는 모두 부모 노드에 자식 노드를 추가하는 메서드, 하지만 메서드에서도 몇가지 차이점이 존재한다.

### 👉 append()

append 메서드를 활용하면 노드 객체(node object)나 DOMString(text)를 사용할 수 있습니다. 또 한번에 여러 개의 자식 요소를 설정할 수 있습니다.

- 노트 객체 사용 예시

```javascript
// 노드 객체 삽입
const parent = document.createElement("div");
const child = document.createElement("p");

parent.append(child);

// 결과
// <div> <p> </p> </div>
```

- 문자열(DOMString) 사용 예시

```javascript
// DOMString 삽입
const parent = createElement("div");
parent.append("아이스크림");

// 결과
// <div>아이스크림</div>
```

- 여러 개의 자식 요소를 설정하는 예시

```javascript
const div = document.createElement("div");
const span = document.createElement("span");
const p = document.createElement("p");

document.body.append(div, "Hello", span, p);

// 결과
<body>
  <div></div>
  Hello
  <span></span>
  <p></p>
</body>;
```

- append 메서드는 return 값을 반환하지 않습니다.

```javascript
const div = document.createElement("div");
const span = document.createElement("span");
const p = document.createElement("p");

console.log(document.body.append(div, "Hello", span, p)); // undefined
```

### appendChild()

- 노드 객체 사용 예시
  appendChild 메서드는 append 메서드와는 다르게 오직 node 객체만 받을 수 있다. append는 여러 개의 노드와 문자를 추가할 수 있는 반면에 appendChild 메서드는 한번에 오직 하나의 노드만을 추가할 수 있다.

```javascript
const parent = document.createElemnet("div");
const child = document.createElement("p");

parent.appendChild(child);

// 결과
// <div><p></p></div>
```

- 문자열 (DOMString) 사용 예시
  appendChild 메서드는 DOMString을 넣을 경우 에러가 발생한다.

```javascript
// DOMString 삽입
const parent = document.createElement("div");

parent.appendChild("아이스크림");
// Uncaught TypeError: Faild to execute 'appendChild' on 'Node':parameter 1 is not of type 'Node'
```

- appendChild 메서드는 return 값을 반환합니다.

```javascript
const div = document.createElement("div");
const span = document.createElement("span");

console.log(document.body.appendChild(div)); // div(Node object)
```

## 📌 3. Element 조회

**querySelector()** 는 특정 name,id,class를 제한하지 않고 css선택자를 사용하여 요소를 찾습니다.

같은 id 또는 class 일 경우 스크립트의 최상단 요소만 로직에 포함합니다.

- querySelector(#id) => id 값 id를 가진 요소를 찾습니다.
- querySelector(.class) => class 값 class를 가진 요소를 찾습니다.

`querySelector` 에 `.tweet` 을 첫 번째 인자로 넣으면, 클래스 이름이 tweet 인 HTML 엘리먼트 중 첫 번째 엘리먼트를 조회할 수 있습니다.

```javascript
const oneTweet = document.querySelector(".tweet");
```

클래스 이름이 tweet인 요소가 여러개 있다. 변수 onetweet 에 할당된 요소는 하나뿐이다. 여러개의 요소를 가져오기 위해 querySelectorAll 을 사용한다.

```javascript
const tweets = document.querySelectorAll(".tweet");
```

CREATE에서 생성한 div 요소를 container에 넣을 준비를 마쳤습니다. 다음 코드를 입력하면, container의 맨 마지막 자식 요소로 tweetDiv를 추가합니다.

```javascript
const container = document.querySelector("#container");
const tweetDiv = document.createElement("div");
container.append(tweetDiv);
// tweetDiv를 container의 마지막 자식 요소로 추가합니다.
```

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/VnqXiZ-_4-1618885682009.gif)

- tweetDiv를 container의 마지막 자식 요소로 추가한 모습

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/PHmvd-SCC-1597040922206.gif)

- id가 container인 엘리먼트의 마지막 자식 요소로 tweetDiv를 추가합니다.

---

- getElementById()

  => Element의 id로 접근할 수 있다.

- getElementByClassName() / getElementsByClassName()

  => Element의 class 이름으로 접근할 수 있다.

## 📌 4.Element update

**_ClassList.add()_**  
Element에 class name을 추가할 수 있다.

```javascript
let aElement = document.createElement("a");

aElement.classList.add("name");
```

**_textContent_**

- Element 및 Node에 텍스트를 추가할 수 있는 메서드이다.
  반환값은 문자열 또는 null이다.
- 선택한 요소에서 HTML 요소를 제거한 순수한 텍스트 데이터의 값

```javascript
aElement.textContent = "awesome";
```

**_innerHTML_**

```javascript
aElement.innerHTML = "awesome";
```

- innerHTML는 이름 그대로 HTML을 반환한다. HTML tag를 직접 삽입하여 실행하는 형태의 메소드는 늘 이런 위험을 가지고 있다.
- 선택한 요소의 HTML 태그를 그대로 제공하여 보안에 취약(사용자로부터 전달받은 콘텐츠를 추가할 때는 사용하지 않는 것이 좋음)

## 📌 5. Element 제거

**_removeChild() VS remove()_**  
자식 노드를 삭제하는 메서드이다.  
remove()는 노드를 메모리에서 삭제하고 종료한다.
반면에 removeChild()는 메모리에 해당 노드는 그대로 존재하며, 부모 노드와의 부모-자식관계를 끊어 DOM 트리에서 제거한다. 최종적으로는 관계를 끊은 해당 노드의 참조를 반환한다.

![Alt text](https://velog.velcdn.com/images%2Fbining%2Fpost%2F4ff9355a-14dd-42bd-b6ae-0fd1168b5147%2Fimage.png)

```javascript
const container = document.querySelector("#container");
const tweetDiv = document.createElement("div");
container.append(tweetDiv);
```

```javascript
tweetDiv.remove(); // append 했던 엘리먼트를 삭제할 수 있다.
```
