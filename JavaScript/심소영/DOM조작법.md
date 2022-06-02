# DOM 조작법

### DOM을 JavaScript로 조작하여 HTML Element를 추가하거나 삭제, 혹은 내용을 변경할 수 있다.


***
## CRUDA에 따른 DOM 조작 메소드

#### **CREATE** 
자바스크립트를 이용해 DOM에 HTML Element를 추가   

1. createElement : 새로운 HTML 요소 생성
```js
    const divBox = document.createElement('div')
```
     
#### **READ** 
자바스크립트로 DOM을 조작해 HTML Element 조회한다.
1. querySelector : 첫 번째 요소를 가져온다.
  
2. querySelectorAll : 여러 개의 엘리먼트를 한 번에 가져올 수 있다.   
  querySelectorAll로 가져온 엘리먼트들은 NodeList라는 유사배열(Array-like Object)로, 배열처럼 for문을 사용할 수 있다.
```js
const allBox = document.querySelectorAll('.box')
```


#### **UPDATE** 
자바스크립트로 DOM을 조작해 HTML Element를 변경(수정)한다.
1. textContent : textContent를 변경해 내용을 추가할 수 있다.
```js
    divBox.textContent = "내용 추가"
```

1. id : 특정한 태그를 제어
  
2. classList :  class를 추가하거나 삭제할 수 있다.
```js
    divBox.classList.add('box-style')
```
  
1. setAttribute : 요소의 속성값을 설정해준다.
   
#### **DELETE** 
1. remove : 요소를 삭제한다.
```js
    divBox.remove()
```

2. removeChild : 자식 요소를 삭제한다.
```js
    Body.removeChild()
```
  
3. innerHTML = "" : document.getElementById 메서드를 함께 사용해 HTML Element에 접근, 수정.
  
4. textContent = "" : 텍스트를 추가하고 / 해당 Element의 텍스트값을 반환한다.
    
#### **APPEND** 
HTML Element를 부모 엘리먼트의 자식 엘리먼트로 넣을 수 있다.

1. append : 부모노드에 자식노드를 추가하는 메서드.   
            노드객체나ㅏ DOMstring(text)를 사용할 수 있다.   
            한번에 여러개의 자식 요소 설정이 가능하다.   
            return 값을 반환하지 않는다.
[예시코드1]
```js
    //Node object 삽입
    const parent = document.createElement('div');
    const child = document.creatElement('p');

    parent.append(child);

    //<div><p></p></div>
```

[예시코드2]
```js
    //DOMString 삽입
    const parent = document.creatElement('div');
    parent.append('append 예시')

    //<div>append 예시</div>
```
  
[예시코드3]
```js
    //여러개의 자식요소 설정 예시
    const div = document.createElement('div')
    const span = document.createElement('span')
    const p = document.createElement('p')

    document.body.append(div,'hello',span,p);

    //결과
    <body>
     <div></div>
     hello
     <span></span>
     <p></p>
    </body>
```


2. appendChild :  부모노드에 자식노드를 추가하는 메서드.   
                append메서드와 다르게 오직 Node객체만 받는다.   
                 또햔 한번에 하나의 노드만 추가할 수 있다.
                

***
## 속성에 따른 분류
### 유용한 DOM 엘리먼트 속성 

- tagName : 엘리먼트의 태그명 반환
  
- textContent : 노드의 텍스트 내용을 설정하거나 변환

- nodeType : 노드의 노드 유형을 숫자로 변환
  
### DOM 탐색 속성
- childNodes : 엘리먼트의 자식 노드의 노드 리스트 반환 ( textNode, 주석 노드 포함)
  
- firstChild : 엘리먼트의 첫번째 자식 노드 반환
- firstElementChild : 첫번째 자식 엘리먼트 반환
- parentElement : 엘리먼트의 부모 엘리먼트 반환
- nextSibling : 동일한 노드 트리 레벨에서 다음 노드 반환
- nextElementSibling : 동일한 노드 트리 레벨에서 다음 엘리먼트 반환

### DOM 조작 메소드

- removeChild() : 엘리먼트의 자식 노드 제거
  
- appendChild() : 마지막 자식 노드를 추가
- insertBefore() : 기존 자식노드 앞에 새 자식 노드 추가
- cloneNode() : 엘리먼트의 자식 노드 복제
- replaceChild() : 엘리먼트의 자식 노드 바꾸기
- closest() : 상위로 올라가면서 가장 가까운 엘리먼트를 반환
- HTML을 문자열로 처리해주는 DOM 속성 / 메소드
- innerText : 지정된 노드와 모든 자손의 텍스트 내용을 설정하거나 반환
- innerHTML : 지정된 엘리먼트의 내부 HTML을 설정하거나 반환
- innsertAdjacentHTML() : HTML로 텍스트를 지정된 위치에 삽입

***


## 지양되는 방법

요소생성시 innerHTML 사용 지양.

[예시코드]
```js
let aElement = document.createElement('a')
aElement.id = 'javascipt'
aElement.innerHTML = 'perfect' 
//HTML tag를 직접 삽입하여 실행시키는 메소드는 <script> tag를 통한 해킹의 우려가 있음
```
