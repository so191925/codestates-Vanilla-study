# DOM 조작방법

## 📌 요소 노드 읽는 방법 (READ)

### 🧩 id를 이용해서 요소 노드 읽는 방법   
**📋 Doucument.prototype.getElementById("id 이름")**
```HTML
<!DOCTYPE html>
<!--id는 고유한 값으로 하나의 노드만 탐색한다.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul>
            <li id="red">Red</li>
            <li id="orange">Orange</li>
            <li id="yellow">Yellow</li>
        </ul>
    </body>
    <script>
        // id를 이용하여 요소 노드를 획득
        const $red = document.getElementById("red");
        console.log($red);
    </script>
</html>
```
### 🧩 태그 이름으로 요소 노드 읽는 방법   
**📋 Document.prototype.getElementsByTagNames("태그 이름")**   
**📋 Element.prototype.getElementsByTagNames("태그 이름")**

```HTML
<!DOCTYPE html>
<!--해당 노드의 부터 시작하여 후손 노드만 모두 탐색하여 조건에 맞게 반환한다.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="color">
            <li id="red">Red</li>
            <li id="orange">Orange</li>
            <li id="yellow">Yellow</li>
        </ul>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        // document는 DOM 트리의 루트 노드로써 DOM전체에서 탐색한다.
        const $li = document.getElementsByTagName("li");
        const $animals = document.getElementById("animals");
        // id가 animals인 요소 노드부터 탐색한다.
        const $animalsli = $animals.getElementsByTagName("li");
        // 결과: HTMLCollection(5) [li#red, li#orange, li#yellow, li#dog ...]
        console.log($li);
        // 결과: HTMLCollection(2) [li#dog, li#cat, dog: li#dog, cat: li#cat]
        console.log($animalsli);
    </script>
</html>
```

### 🧩 class를 이용해서 요소 노드 읽는 방법   
**📋 Document.prototype.getElementsByClassName("클래스 값")**   
**📋 Element.prototype.getElementsByClassName("클래스 값")**

```HTML
<!DOCTYPE html>
<!--해당 노드의 부터 시작하여 후손 노드만 모두 탐색하여 조건에 맞게 반환한다.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul class="color">
            <li class="color red">Red</li>
            <li class="color orange">Orange</li>
            <li class="color yellow">Yellow</li>
        </ul>
        <ul id="animals">
            <li class="animals dog">Dog</li>
            <li class="animals cat">Cat</li>
        </ul>
    </body>
    <script>
        // class 이름중 color가 들어가있는 모든 요소 노드 탐색
        const $color = document.getElementsByClassName("color");
        // class 이름중 color와 red가 들어가있는 모든 요소 노드 탐색
        const $red = document.getElementsByClassName("color red");
        // id가 animals인 요소 노드 탐색
        const $animals = document.getElementById("animals");
        /* id가 animals인 요소 노드의 자식중 
           class 이름에 animals가 들어가있는 요소 노드 탐색 */
        const $animalsli = $animals.getElementsByClassName("animals");
        // 결과 : HTMLCollection(4) [ul.color, li.color.red, li.color.orange ...]
        console.log($color);
        // 결과 : HTMLCollection [li.color.red]
        console.log($red);
        // 결과 : HTMLCollection(2) [li.animals.dog, li.animals.cat]
        console.log($animalsli);
    </script>
</html>
```

### 🧩 CSS Selector를 이용한 요소 노드 읽는 방법   
**📋 Document.querySelector("CSS 선택자 문법")**   
**📋 Element.querySelector("CSS 선택자 문법")**   
**📋 Document.querySelectorAll("CSS 선택자 문법")**   
**📋 Element.querySelectorAll("CSS 선택자 문법")**   </br> </br>
**🔥 제일 많이 사용하는 요소 노드 접근 방법**   
**querySelector는 조건에 맞는 첫번째 노드만 반환하지만 querySelectorAll은 조건에 맞는 모든 노드를 NodeList에 담아서 반환한다.**

```CSS
/* 전체 선택자: 모든 요소를 선택 */
*

/* 태그 선택자: 모든 태그를 선택 */
li

/* id 선택자: id 값이 color인 요소 모두 선택 */
#color

/* class 선택자: class 값이 color인 요소 모두 선택 */
.color

/* 속성 선택자: input 요소 중 type 속성이 text인 요소 모두 선택 */
input[type=text]

/* 후손 선택자: ul 요소의 후손중 li 태그인 요소 모두 선택 */
ul li

/* 자식 선택자: ul 요소의 자식중 li 태그인 요소 모두 선택 */
ul > li

/* 인접 형제 선택자: div 요소의 형제 요소 중에 span 이며 바로 뒤의 요소 반환 */
div + span

/* 일반 형제 선택자: div 요소의 형제 요소 중에 span 모두 선택 */
div ~ span

/* 가상 클래스 선택자: 나중에 사용할 때 찾아보기 */
a:hover

/* 가상 요소 선택자: 나중에 사용할 때 찾아보기 */
a::before
```

```HTML
<!DOCTYPE html>
<!--해당 노드의 부터 시작하여 자식 노드만 모두 탐색하여 CSS 선택자에 맞게 반환한다.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="nav-container1">
            <li class="nav1">nav1</li>
            <li class="nav2">nav2</li>
            <ul id="nav-container2">
                <li class="nav3">nav3</li>
                <li class="nav4">nav4</li>
            </ul>
        </ul>
        <input type="number" placeholder="number">
        <input type="text" placeholder="text">
        <input type="text" placeholder="text">
        <div class="form">
            <div></div>
            <span class="text1">Hello</span>
            <span class="text2">World</span>
        </div>
    </body>
    <!--
        querySelectorAll은 조건에 맞는 노드를 전부 NodeList에 담아서 모아 반환한다.
        querySelector는 조건에 맞는 노드중 첫 번째 요소만 반환한다.
    -->
    <script>
        // 모든 요소 노드 탐색
        const $all = document.querySelectorAll("*");
        // 모든 li 태그 요소만 탐색
        const $liTag = document.querySelectorAll("li");
        // id가 #nav-container1인 모든 요소 탐색
        const $navContaniner1 = document.querySelectorAll("#nav-container1");
        // class 값이 .nav1인 모든 요소 탐색
        const $nav1 = document.querySelectorAll(".nav1");
        // input 태그이면서 type 속성의 값이 text인 모든 요소 탐색
        const $input_text = document.querySelectorAll("input[type=text]");
        // 모든 ul 요소의 후손중에 모든 li 요소 탐색
        const $liAll = document.querySelectorAll("ul li");
        // id가 #nav-container2 첫번째 요소 탐색
        const $navContaniner2 = document.querySelector("#nav-container2");
        // $navContaniner2의 ul 태그에서 자식노드인 모든 li 요소 탐색
        const $li = $navContaniner2.querySelectorAll("ul > li");
        // class 값이 .form 첫번째 요소 탐색
        const $form = document.querySelector(".form");
        // $form의 후손중에서 div와 형제인 노드중 첫번째 span 요소 탐색
        const $span = $form.querySelectorAll("div + span");
        // $form의 후손중에서 div와 형제인 노드중 모든 span 요소 탐색
        const $spanAll = $form.querySelectorAll("div ~ span");

        // 결과 : NodeList(19) [html, head, meta, body, ...]
        console.log($all);
        // 결과 : NodeList(4) [li.nav1, li.nav2, li.nav3, li.nav4]
        console.log($liTag);
        // 결과 : NodeList [ul#nav-container1]
        console.log($navContaniner1);
        // 결과 : NodeList [li.nav1]
        console.log($nav1);
        // 결과 : NodeList(2) [input, input]
        console.log($input_text);
        // 결과 : NodeList(4) [li.nav1, li.nav2, li.nav3, li.nav4]
        console.log($liAll);
        // 결과 : NodeList(2) [li.nav3, li.nav4]
        console.log($li);
        // 결과 : <div class="form>...</div>
        console.log($form);
        // 결과 : NodeList [span.text1]
        console.log($span);
        // 결과 : NodeList(2) [span.text1, span.text2]
        console.log($spanAll);
    </script>
</html>
```

## 📌 HTMLCollection과 NodeList의 차이점

요소를 취득하는 방법중에 NodeList로 반환하는 메소드는 querySelectorAll 밖에 없으며 차이점은 HTMLCollection은 요소 노드의 id, name 속성값으로 접근이 가능하며 Live 객체로 사용된다. 하지만 NodeList의 노드는 과거의 상태를 유지하며 Non-Live 객체이다. 하지만 Node.prototype.childNodes가 반환하는 NodeList 객체만은 Live 객체로 사용된다.

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="container">
            <li id="li1" name="nav1">nav1</li>
            <li id="li2" name="nav2">nav2</li>
            <li id="li3" name="nav3">nav3</li>
        </ul>
    </body>
    <script>
        // HTMLCollection으로 불러오기
        const $HTML = document.getElementsByTagName("li");
        // NodeList로 불러오기
        const $node = document.querySelectorAll("li");
        // 결과 : HTMLCollection(3) [li#li1, li#li2, li#li3, …]
        console.log($HTML);
        // 결과 : NodeList(3) [li#li1, li#li2, li#li3]
        console.log($node);
        // 결과 : <li id="li1" name="nav1">...</li>
        console.log($HTML.nav1);
        // 결과 : <li id="li2" name="nav2">...</li>
        console.log($HTML.li2);
        // 결과 : 에러 출력
        console.log(node.nav1);
    </script>
</html>
```

```HTML
<!DOCTYPE html>
<!--Live 객체 의미 해석-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <ul id="container">
            <li class="red">nav1</li>
            <li class="red">nav2</li>
            <li class="red">nav3</li>
        </ul>
    </body>
    <script>
        const $HTML = document.getElementsByClassName("red");
        // 코드를 순회하면 nav2는 바뀌지 않는다. 이유는 살아있는 객체이기 때문이다.
        // 살아있는 객체란 자료구조 Stack에서 for문을 사용 못하는 이유와 같다. 
        // 배열의 길이가 변하기 때문이다.
        for(let i = 0; i < $HTML.length; i++) $HTML[i].className = "blue";
    </script>
</html>
```

**🔥 해결법은 while문을 사용하거나 HTMLCollection이 이터러블 프로토콜을 준수하여 배열로 치환후 사용한다.**

## 📌 노드 탐색

### 🧩 자식 노드 탐색   
**📋 Node.prototype.childNodes (메소드가 아니라 프로퍼티)**   
**📋 Element.prototype.children (메소드가 아니라 프로퍼티)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $animals = document.querySelector("#animals");
        // node는 텍스트 노드도 포함되기 때문에 텍스트 노드도 포함되어 있다.
        const $nodeList = $animals.childNodes;
        // Element 프로퍼티라서 요소 노드만 포함된다.
        const $HTMLCollection = $animals.children;
        // 결과 : NodeList(5) [text, li#dog, text, li#cat, ...]
        console.log($nodeList);
        // 결과 : HTMLCollection(2) [li#dog, li#cat, ...]
        console.log($HTMLCollection);
    </script>
</html>
```

### 🧩 부모 노드 탐색
**📋 Node.protype.parentNode (메소드가 아니라 프로퍼티)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $dog = document.querySelector("#dog");
        const $parent = $dog.parentNode;
        // 결과 : <ul id="animals">...</ul>
        console.log($parent);
    </script>
</html>
```

### 🧩 형제 노드 탐색   
**📋 Element.prototype.previousElementSibling (메소드가 아니라 프로퍼티)**   
**📋 Element.prototype.nextiousElementSibling (메소드가 아니라 프로퍼티)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="pig">Pig</li>
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $dog = document.querySelector("#dog");
        const $Sibling1 = $dog.previousElementSibling;
        const $Sibling2 = $dog.nextElementSibling;
        // 결과 : <li id="pig>...</li>
        console.log($Sibling1);
        // 결과 : <li id="cat>...</li>
        console.log($Sibling2);
    </script>
</html>
```

## 📌 요소 노드의 텍스트 조작방법 (UPDATE)

**📋 HTMLElement.prototpe.innerText (메소드가 아니라 프로퍼티)**   
**📋 Node.prototype.textContent (메소드가 아니라 프로퍼티)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Hello
            <span id="sub-title">World!</span>
        </div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // 결과 : HEY로 문자열 바뀜
        $div.textContent = "HEY";
        // 결과 : HEY -> Hello로 바뀜
        $div.innerText = "Hello";
    </script>
</html>
```

**🔥 차이점은 innerText는 CSS에 종속적임 CSS를 고려해야함으로 성능이 textContent보다 느리지만 많은 코드에서 innerText를 사용함으로 사용유무는 개발자 판단이라고 생각함**

## 📌 DOM HTML 조작 (UPDATE)

**📋 Element.prototype.innerHTML (메소드가 아니라 프로퍼티)**   
장점 : 구현이 간단하고 코드가 직관적이다.   
단점 : HTML의 데이터를 문자열로 직접 입력하기 때문에 XSS에 취약하다. (보안)   

**🔥 되도록이면 노드를 생성해서 자식노드로 추가하여 사용**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // 자식노드로 추가된다. 직접 코드를 작성해서 직관적
        $div.innerHTML = `<h2>Hello</h2>`
        // 결과 <div id="title> <h2>Hello</h2> </div>
        console.log($div);
    </script>
</html>
```

**📋 Element.prototype.insertAdjacentHTML("추가할 위치", "HTML 코드")**   
장점 : 구현이 간단하고 형제노드로도 추가가 가능하며 코드가 직관적이다.   
단점 : HTML의 데이터를 문자열로 직접 입력하기 때문에 XSS에 취약하다. (보안)  

<p align="center">
  <img src="./img/insertAdjacentHTML.PNG" alt="html" width="500px" height="200px"/>
</p>

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // 자식노드로 추가
        $div.insertAdjacentHTML("afterbegin", `<h2>Title</h2>`);
        // 형제노드로 추가
        $div.insertAdjacentHTML("afterend", `<div id="subtitle">Subtitle<div>`);
        // body 태그 결과확인
        console.log(document.body);
    </script>
</html>
```

## DOM 조작 (CREATE, UPDATE, DELETE)

### 🧩 노드 생성   
**📋 Document.prototype.createElement("생성할 태그이름")**   
**📋 Document.prototype.createTextNode("생성할 문자열")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <!--DOM 조작-->
    </body>
    <script>
        // div 태그 생성
        const $div = document.createElement("div");
        // 텍스트 노드 생성
        const $divText = document.createTextNode("Hello");
        // 텍스트 노드는 무조건 요소 노드의 자식이므로 자식노드로 넘겨줌
        $div.appendChild($divText);
        // body 태그에 직접 자식으로 상속
        document.body.appendChild($div);
        // 결과 : <body>...</body>
        console.log(document.body);

        /* 위의 코드와 동일하게 동작 원하는 방법으로 사용하면 됨
        const $div = document.createElement("div");
        // $div.textContent = "Hello";
        $div.innerText = "Hello";
        document.body.appendChild($div);
        console.log(document.body);
        */
    </script>
</html>
```

### 🧩 노드 삽입   
**📋 Node.prototype.appendChild(추가할 노드)**   
**📋 Node.prototype.insertBefore(추가할 노드, 기준점 노드)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
        <div id="content"></div>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $content = document.querySelector("#content");
        const $span = document.createElement("span");
        $span.innerText = "Top";
        // appendChild는 무조건 마지막 자식노드로 위치하게 된다.
        $title.appendChild($span);
        const $div = document.createElement("div");
        $div.innerText = "Mid";
        $content.innerText = "Bottom";
        // 기준점 노드 앞에 위치하게 된다 기준점 노드에 null을 넣는 경우 맨뒤에 추가.
        // document.body.insertBefore($div, null); 
        document.body.insertBefore($div, $content);
        // 결과 : <body>...</body>
        console.log(document.body);
    </script>
</html>
```

### 🧩 노드 교체   
**📋 Node.prototype.replaceChild(추가할 노드, 기존 노드)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Title</div>
        <div id="content">Content</div>
    </body>
    <script>
        // id가 content인 요소 노드에 접근
        const $content = document.querySelector("#content");
        // div 요소 노드 생성
        const $subtitle = document.createElement("div");
        // 텍스트 노드를 Subtitle로 생성
        $subtitle.innerText = "Subtitle";
        // 노드 교체
        document.body.replaceChild($subtitle, $content);
    </script>
</html>
```

### 🧩 노드 삭제   
**📋 Element.prototype.remove()**   
**📋 Node.prototype.removeChild(삭제할 자식 노드)**

```HTML
<!DOCTYPE html>
<!-- 요소 노드는 라이브 객체이기 때문에 버튼을 눌러 console에서 확인후 다시 누르기  -->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Title</div>
        <div id="content">Content</div> <br />
        <button id="btn" type="button">console.log</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $content = document.querySelector("#content");
        const $btn = document.querySelector("#btn");
        // removeChild를 사용하여 텍스트 노드를 제거하는 함수
        const removeContentText = () => {
            const [ textNode ] = $content.childNodes;
            // 자식의 요소만 삭제가 가능하다.
            $content.removeChild(textNode);
            console.log(document.body);
            return;
        }
        // remove를 사용하여 요소 노드와 요소 노드의 자식까지 제거
        const removeTitle = () => {
            // 해당 요소 노드와 자식 노드까지 제거
            $title.remove();
            console.log(document.body);
        };
        // 순차적으로 실행하기 위해서 제너레이터 사용
        const step = function * () {
            yield removeTitle();
            yield removeContentText();
        }();
    
        $btn.addEventListener("click", () => {
            const check = step.next();
            // 오류 방지
            if(check.done) return;
        });
    </script>
</html>
```

**🔥 remove 메소드는 요소 노드와 해당 자식 노드까지 제거**   
**🔥 removeChild 메소드는 자식 노드만 제거**

### 🧩 노드 복사     
**📋 Node.prototype.cloneNode([ deep : true | false ])**

**① 공식문서등을 확인할 때 메소드 안에 인자값이 [] 이런형태안에 있는것은 필수가 아니라는 뜻이다.**   
**② default 값은 false 이다. 인자에 아무것도 없이 사용하면 기본값 적용**   
**③ 깊은 복사란 Depth안에 있는 모든 값을 복사한다는 의미이다.**   
**④ 원시값과 참조값의 얇은복사, 깊은복사 개념과 참조값안에서 얇은복사 깊은복사 개념은 다르다.**

```JavaScript
// 객체 안의 프로퍼티 값이 객체를 가지고 있을 경우 Depth는 한단계 올라간다.
// 모든 참조값이 같은 개념 (배열, 객체)
const Object = {
    // 1 Depth
    A: 1,
    B: {
        // 2 Depth
        C: 2,
        D: 2,
        E: {
            // 3 Depth
            F: 3,
            G: 3
        }
    }
}
```

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <!--자식노드부터 2 Depth 시작 텍스트 노드도 자식노드에 포함된다.-->
        <div id="title"> Hello
            <span>World</span>
        </div>
    </body>
    <script>
        const $title = document.querySelector("#title");
        // 얇은 복사 $title.cloneNode(false)랑 표현이 같다.
        const shallowCopy = $title.cloneNode(); 
        // 깊은 복사
        const deepCopy = $title.cloneNode(true);
        // 결과 : <div id="title"></div> 요소 노드만 복사
        console.log(shallowCopy);
        // 결과 : <div id="title">...</div> 요소 안에 있는 자식노드도 모두 복사
        console.log(deepCopy);
    </script>
</html>
```

## 📌 요소 노드의 속성 노드 조작방법 (CREATE, READ, UPDATE, DELETE)

- 속성 노드의 값 접근   
**📋 Element.prototype.getAttribute("속성 노드 이름")**
- 속성 노드의 값을 수정  
**📋 Element.prototype.setAttribute("속성 노드 이름", "수정할 값")**
- 속성 노드의 값을 삭제   
**📋 Element.prototype.removeAttribute("속성 노드 이름")**
- 속성 노드의 값이 존재하는지 확인
**📋 Elemnet.prototype.hasAttribute("속성 노드 이름")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text" value="Default"> <br/> <br/>
        <button type="button">console.log</button>
    </body>
    <script>
        const $input = document.querySelector("#input");
        const $btn = document.querySelector("button");
        // 순차적으로 실행하기 위해서 제너레이터 사용
        const step = function * () {
            // value 속성 노드의 값을 가져온다.
            yield $input.getAttribute("value");
            // value 속성 노드의 값을 수정한다.
            $input.setAttribute("value", "Change");
            // value 속성 노드의 값을 가져온다
            yield $input.getAttribute("value");
            // value 속성 노드를 제거한다.
            $input.removeAttribute("value");
            // input 요소 노드의 속성 노드에 value가 있는지 확인한다.
            yield $input.hasAttribute("value");
        }();

        $btn.addEventListener("click", () => {
            const check = step.next();
            // 오류 방지
            if(check.done) return;
            else console.log(check.value);
        });
    </script>
</html>
```

## 📌 HTML 속성과 DOM의 프로퍼티

HTML 속성은 초기의 속성 노드의 값에 대응한다. 처음에 HTML 태그안에 적은 속성값을 가지고 있다. 초기값의 접근 하는 방법은 getAttribute() 메소드를 이용해서 값에 접근하거나 setAttribute()로 초기값을 수정하는 방법이 있다.

DOM의 프로퍼티는 사용자가 인터페이스를 이용해서 바꾼 최신상태의 값을 가지고 있다.

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text" value="Default"> <br/> <br/>
        <button id="default" type="button">Default</button>
        <button id="change" type="button">Change</button>
    </body>
    <script>
        const $input = document.querySelector("#input");
        const $default = document.querySelector("#default");
        const $change = document.querySelector("#change");
        // HTML의 속성으로 접근
        $default.addEventListener("click", () => {
            // input을 변경해도 HTML 태그 안에 있는 초기값을 가지고 있다.
            console.log($input.getAttribute("value"));
        });
        //DOM 프로퍼티로 접근
        $change.addEventListener("click", () => {
            // 현재 최신값으로 변경된다.
            console.log($input.value);
        });
    </script>
</html>
```
**🔥 DOM의 프로퍼티로 접근하는 방법은 직접 요소 노드의 속성 노드의 이름을 객체 프로퍼티로 접근한다.**   
**🔥 HTML의 속성으로 접근하는 방법은 메소드를 이용해 접근한다.**

## 📌 요소 노드의 data 이용

**생성 방법 : 해당 요소 노드에 속성 노드를 추가 형식은 data-string 형태**   
**접근 방법 : 해당 요소 노드에 접근하여 객체 프로퍼티(dataset)로 접근 카멜표기법 준수**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="list">
            <!-- 생성 -->
            <li data-animals-index="0">Cat</li>
        </ul>
    </body>
    <script>
        const $li = document.querySelector("li");
        // 접근 방법 결과 : "0";
        console.log($li.dataset.animalsIndex);
    </script>
</html>
```

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="list">
            <li data-animals-index="0">Cat</li>
            <li>Dog</li>
        </ul>
    </body>
    <script>
        const $li = document.querySelectorAll("li");
        const [$cat, $dog] = $li;
        // 이런식으로 접근도 가능하다.
        $dog.setAttribute("data-animals-index", "1");
        // 결과 : "1"
        console.log($dog.dataset.animalsIndex);
    </script>
</html>
```

**🔥 보통사용 방법은 해당 요소 노드의 인덱스를 제공하여 이벤트 위임을 사용하여 해당 요소 노드를 체크하고 CRUD에 이용한다.**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text"> <br/> <br/> 
        <button id="add">추가</button> <br/>
        <ul id="list">

        </ul>
    </body>
    <script>
        // 동물의 이름을 입력 받아 저장할 배열 선언
        const animals = [];
        // input의 동물의 이름을 전송하기 위해 버튼 요소 접근
        const $addbtn = document.querySelector("#add");
        // 이벤트 위임을 위해서 id가 list인 요소에 접근
        const $list = document.querySelector("#list");
        // 페이지를 계속 고쳐줄 함수 생성
        const render = () => {
            // animals의 이름을 받아서 HTML요소로 바꾸기
            const makeHTML = animals.map((item, index) => {
                // index를 받아서 data에 index로 사용하기 위해 지정
                return `<div data-animals-index=${index} style="display: flex">
                    <li>${item}</li>
                    <button id="update" style="margin-left: 10px">수정</button>
                    <button id="remove" style="margin-left: 10px">삭제</button>
                </div>`
            });
            // 해당 배열 내용을 문자열로 치환후 HTML 조작
            $list.innerHTML = makeHTML.join('');
        }
        $addbtn.addEventListener("click", () => {
            // input 요소에 접근
            const $input = document.querySelector("#input");
            // animals 배열에 해당 동물을 저장
            animals.push($input.value);
            // input 초기화
            $input.value = null;
            // 페이지 수정
            render();
        });
        // 이벤트 위임
        $list.addEventListener("click", (e) => {
            // 해당 동물의 인덱스 번호를 이벤트를 위임해논 요소의 dataset에 접근 
            const index = e.target.closest("div").dataset.animalsIndex;
            // 클릭한 요소가 id가 update 버튼인지 확인
            if(e.target.id === "update") {
                // 수정받는 값을 변수에 저장
                const updateText = prompt("수정할 동물의 이름을 입력하세요.");
                // 해당 배열인덱스에 접근하여  값 수정
                animals[index] = updateText;
                // 페이지 수정
                render();
            // 클릭한 요소가 id가 remove 버튼인지 확인
            } else if(e.target.id === 'remove') {
                // 해당 배열에서 요소 삭제
                animals.splice(index, 1);
                // 페이지 수정
                render();
            }
        });
    </script>
</html>
```
**🔥 Element.prototype.closest("해당 태그")는 처음으로 만난 해당 태그의 부모노드를 반환한다.**   
**🔥 이벤트 위임과 e.target은 이벤트 부분에서 확인하기**

```HTML
<!DOCTYPE html>
<!-- innerHTML XSS 단점으로 노드의 상속을 이용해서 만든 코드 -->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .form {
            display: flex;
        }
        .blank {
            margin-left: 10px;
        }
    </style>
    <body>
        <input id="input" type="text"> <br/> <br/> 
        <button id="add">추가</button> <br/>
        <ul id="list">

        </ul>
    </body>
    <script>
        const animals = [];
        const $addbtn = document.querySelector("#add");
        const $list = document.querySelector("#list");
        // 노드의 자식들을 모두 지워주기 위해서 reset 함수 생성
        const reset = () => {
            // childeNodes는 라이브객체이므로 배열로 바꿔서 사용
            const child = [...$list.childNodes];
            // 해당 자식 요소 노드 전부 삭제
            child.forEach((item) => item.remove());
        }
        // 페이지를 새로 고쳐줄 함수
        const render = () => {
            // 페이지를 고치기 전에 reset함수 실행
            reset();
            // 의미없는 태그인 div를 한번더 생성하지 않기 위해 생성
            const $container = document.createDocumentFragment();
            // 해당 배열의 요소마다 실행할 코드
            animals.forEach((item, index) => {
                // 노드 생성 하고 속성 생성 클래스이름 생성으로 CSS 적용
                const $div = document.createElement("div");
                const $li = document.createElement("li");
                const $updateBtn = document.createElement("button");
                const $removeBtn = document.createElement("button");
                $updateBtn.id = "update";
                $updateBtn.className = "blank";
                $updateBtn.innerText = "수정";
                $removeBtn.id = "remove";
                $removeBtn.className = "blank";
                $removeBtn.innerText = "삭제";
                $li.innerText = item;
                $div.className = "form";
                $div.setAttribute("data-animals-index", index);
                // 상속 코드
                $div.appendChild($li);
                $div.appendChild($updateBtn);
                $div.appendChild($removeBtn);
                $container.appendChild($div);
            });
            // ul 태그에 추가
            $list.appendChild($container);
        }
        $addbtn.addEventListener("click", () => {
            const $input = document.querySelector("#input");
            animals.push($input.value);
            $input.value = null;
            render();
        });
        $list.addEventListener("click", (e) => {
            const index = e.target.closest("div").dataset.animalsIndex;
            if(e.target.id === "update") {
                const updateText = prompt("수정할 동물의 이름을 입력하세요.");
                animals[index] = updateText;
                render();
            } else if(e.target.id === 'remove') {
                animals.splice(index, 1);
                render();
            }
        });
    </script>
</html>
```

## 📌 요소 노드의 Class 조작

**🔥 class 속성 노드를 조작하는 이유는 CSS 때문이다. 메소드를 이용해서 이벤트위임을 할 때도 사용한다.**   
**🔥 DOM에 접근할 때 className, ClassList인 이유는 JS에서 Class는 예약어이기 때문이다.**

className과 classList는 다른점이 있다. className은 문자열을 반환하는 프로퍼티로 className을 이용해서 className을 바꿀수 있다면 classList는 세부적인 메소드를 제공한다.

### 🧩 클래스 추가   
**📋 Element.prototype.classList.add("클래스 이름")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 class에 red 추가
        $btn.addEventListener("click", () => {
            $title.classList.add("red");
            // 결과 : bold red
            console.log($title.className);
        });
    </script>
</html>
```
**🔥 class는 이름의 공백을 기준으로 CSS를 넣는다. 또한 CSS가 겹치면 class 이름의 마지막 CSS를 참조한다.**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 class에 red blue 추가
        $btn.addEventListener("click", () => {
            $title.classList.add("red")
            $title.classList.add("blue");
            // 결과 : bold red blue 
            // (해당 텍스트 색깔은 파랑색 왜냐면 red보다 blue가 이름이 뒤에있음)
            console.log($title.className);
        });
    </script>
</html>
```
### 🧩 클래스 삭제   
**📋 Element.prototype.classList.remove("클래스 이름")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 class에 red 삭제        
        $btn.addEventListener("click", () => {
            $title.classList.remove("red")
            // 결과 : bold
            console.log($title.className);
        });
    </script>
</html>
```

### 🧩 클래스 확인   
**📋 Element.prototype.classList.contains("클래스 이름")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 class에 요소가 포함되는지 확인
        $btn.addEventListener("click", () => {
            // 결과 : true
            console.log($title.classList.contains("red"));
            // 결과 : false
            console.log($title.classList.contains("blue"));
            // 결과 : true
            console.log($title.classList.contains("bold"));
        });
    </script>
</html>
```

### 🧩 클래스 변경   
**📋 Element.prototype.classList.replace("기존 클래스 이름", "변경할 클래스 이름")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 class에 red를 blue로 변경
        $btn.addEventListener("click", () => {
            $title.classList.replace("red", "blue");
            // 결과 : bold blue
            console.log($title.className);
        });
    </script>
</html>
```

### 🧩 클래스 추출   
**Element.prototype.classList.item(해당 인덱스)**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // 버튼을 누르면 classList의 요소 추출
        $btn.addEventListener("click", () => {
            // 결과 : bold
            console.log($title.classList.item(0));
            // 결과 : red
            console.log($title.classList.item(1));
            // 배열처럼 접근해서 값을 바꾸는건 불가능 add, replace 등등 메소드를 사용
            try {
                $title.classList.item(1) = "blue";
            } catch {
                console.log("error");
            }
        });
    </script>
</html>
```

**🔥 클래스 이름의 요소를 추출 즉 요소의 값을 얻을 떄의 인덱스 처럼 사용하는 번호는 String.split(" ")을 해서 문자열로 반환한거랑 같다고 보면된다.**
