

# DOM
## DOM이란?

>Document Object Model의 약자로,   
HTML 요소를 Object(JavaScript Object)처럼 조작(Manipulation)할 수 있는 Model이다.   
즉, JavaScript를 사용할 수 있으면, DOM으로 HTML을 조작할 수 있다.

## DOM과 Javascript의 차이  

 
 DOM은 JavaScript 언어의 일부가 아니라 웹사이트를 구축하는 데 사용되는 Web API이다.

 DOM은 프로그래밍 언어가 아니지만 DOM이 없으면 JS언어에 웹페이지, HTML문서, SVG 문서 및 구성 요소 부분에 대한 모델이나 개념이 없다. 
 
 문서 전체, 헤드, 문서 내의 테이블, 테이블 헤더, 테이블 셀 내의 텍스트 및 문서의 기타 모든 요소는 해당 문서에 대한 문서 개체 모델의 일부이다.

#

## 📌 개념학습

 HTML에 자바스크립트를 적용하기 위해선 script 태그를 이용한다.
 아래의 경우 HTML 파일과 같은 디렉토리에 존재하는 myScriptFile.js을 불러온다.

[코드] HTML 문서에 포함되는 script 요소
```javascript
    <script src="myScriptFile.js"></script>

    
```
[**script 요소는 등장과 함께 실행된다.**]   

웹 브라우저가 작성된 코드를 해석하는 과정에서 script 요소를 만나면, 웹 브라우저는 HTML 해석을 잠시 멈춥니다. HTML 해석을 잠시 멈춘 웹 브라우저는 script 요소를 먼저 실행한다.    
   
  

>![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/8_QcBAnObnESZ466z95Ns-1652703038855.png)
[그림] 웹 브라우저는 script 요소를 만나면 HTML 해석을 일시정지


# 

## 📌 script에 추가하는 두가지 방식 
1. head 요소에 추가
2. /body가 끝나기 전에 추가
#


## 1. head 요소에 추가

장점 : 웹사이트가 완벽한 형태로 보여진다.   
단점 : JS파일의 사이즈가 크고 인터넷이 느릴 경우, 사용자가 웹사이트를 보는 데까지
        많은 시간이 소요된다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FLvymi%2FbtqGdEJUAMi%2FOol7KH4M8RgLmZ4Mrf4ha1%2Fimg.png)

head에 추가하였을 경우, HTML parsing을 하다가 멈추고 JS를 fetching 및 실행한 후,
HTML parsing을 재개.


[예시코드1]
```js
//1. head 요소에 추가
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
    <!-- script 요소 삽입 위치 -->
    <script src="myScriptFile.js"></script>
  </head>
  <body>
    <div id="msg">Hello JavaScript!</div>
  </body>
</html>
```
#
## 2. /body가 끝나기 전에 추가
장점 : 기본적인 HTML의 컨텐츠를 빠르게 확인 가능.   
단점 : 웹사이트가 JS에 대한 의존도가 높은 경우.
         (즉, 사용자가 의미있는 콘텐츠를 보기 위해서는 JS가 필수라면?)   
        사용자가 정상적인 콘텐츠를 확인하기 위해서는 JS를 서버에서 받아오고 실행하기까지
        기다려야 함.
![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdTApYU%2FbtqGe9WtRBs%2FGerfUZMiXKGUrklI4pYYv1%2Fimg.png)

HTML이 parsing을 끝낸 다음. JS를 fetching 후, 실행.




```js
// 2. /body가 끝나기 전에 추가

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>
  <body>
    <div id="msg">Hello JavaScript!</div>
    <!-- script 요소 삽입 위치 -->
    <script src="myScriptFile.js"></script>
  </body>
</html>

```
#

## DOM구조의 조회
```

javscript에서 DOM은 document객체에 구현되어있다.
따라서 브라우저 속에서 작동되는 자바스크립트코드는 항상 document 객체를 조회할 수 있다.

```
#
# 📌 자식요소 찾기


```js
코드스테이츠 자식요소찾기 수도코드 작성 예제

<html>
  <body>
    <div id="nav"> // function consoleLogAllElement(element)을 이용.
    //nav의 class이름을 console.log 한다.
    //id nav의 자식요소가 있는지 검색한다.logo,menu-wrapper
      <div class="logo"></div>
      //logo의 class명을 console.log 한다.
      //class logo의 자식요소검색.없음
      <div class="">
      //menu-wrapper의 class명을 console.log 한다.
      //menu-wrapper의 자식요소검색. menu,menu,menu,profile-photo
        <div class="menu"></div>   . 동일
        <div class="menu"></div>   .
        <div class="menu"></div>   .
        <div class="profile-photo"></div> .
      </div>  //자식 엘리먼트를 모두 탐색했으므로 함수 실행이 종료.
    </div>   //자식 엘리먼트를 모두 탐색했으므로 함수 실행이 종료.
    <div id="news-contents">
      <div class="news-content-wrapper">
        <div class="news-picture"></div>
        <div class="news-title"></div>
        <div class="news-description"></div>
      </div>
    </div>
    <div id="footer"></div>
  </body>
</html>

```
#
## *개발자 도구에서 자식요소 찾는 방법
```
1. console.dir을 이용해 document.body를 조회한다
2. console.dir(document.body)를 통해 출력된 객체의 키 중에서 children 속성을 찾는다.
3. console.dir(document.body.children) 으로 바로 조회할 수도 있다.
  ```
#
### ** DOM 구조를 조회할 때에는 console.dir 이 유용하다. **  
### ** console.dir 은 console.log 와 달리 DOM을 객체의 모습으로 출력한다. **
```js
[코드] 크롬 개발자 도구에서 document.body를 조회
   
   console.dir(document.body)
   
```   
![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/l8c6M98RS-1597034316742.png)   

[그림]크롬 개발자 도구에서 document.body 조회 예시
#
## * JavaScript에서 자식요소 찾기 접근방식

### 예시자료

```id의 이름이 news-contents 인 <div> 요소의 부모 요소는 무엇인가?```


![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/IqsTy4eUg-1597038630933.png)

```[그림] id가 news-contents 인 <div>요소와 <body> 요소의 관계```

id가 news-contents 인 div 요소는 <body> 요소의 자식 요소이다.   
반대로 <body> 요소는 id가 news-contents div 요소의 부모 요소이다.   
```
따라서 이 관계를 자바스크립트에서 확인할때.   
id가 news-contents 인 엘리먼트를 조회하려면,     
document.body.children 의 첫 번째 요소를 조회한다.
  ```
*document.body 의 children을 조회할 때마다, 매번 document.body 로부터 찾아가는 일은 번거롭기에,
따로 변수 선언을 해서 이 정보를 저장해두면, 주소를 참조하기 때문에 언제든지 접근할 수 있다.   

그에 따른 예시로

![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/rd2xXJ-HV-1597038682624.png)
```js
[예시코드] //변수 newsContents 를 따로 선언하여 id가 news-contents 인 요소를 할당합니다.
```
## *반대로 JavaScript로 부모 요소를 가르키는 속성을 찾고싶을때엔   

### > node.parentElement를 이용한다.
    인터페이스의 읽기 전용 parentElement속성은
    현재 노드의 부모요소 Element를 반환하거나 부모가 없는경우, DOM이 아닐경우 null을 반환한다.
[예시코드]
```js
if (node.parentElement) {
    node.parentElement.style.color = "red";
}
```
#
## 📌 CRUD 와 ARREND

>### C (create) 
>DOM을 JavaScript로 조작하여 HTML Element를 추가할 수 있다.   
>### R (read)
>DOM을 JavaScript로 조작하여 HTML Element를 조회할 수 있다.
>### U (update)
>DOM을 JavaScript로 조작하여 HTML Element를 변경할 수 있다.
>### D (delete)
>DOM을 JavaScript로 조작하여 HTML Element를 삭제할 수 있다. 
>### (APPEND)
>생성한 HTML Element를 부모 엘리먼트의 자식 엘리먼트로 포함할 수 있다. 
#

## 0. append

HTML의 Element를 부모 노드에 포함시키는 메소드
```js
//변수 tweetDiv에 새로운 <div>요소를 할당
const tweetDiv = document.createElement('div')

//변수는 아직 공중부양상태
  //변수 tweetDiv에 담긴 새로운 <div> 요소를 <body> 요소에 append 
  document.body.append(tweetDiv)

>>document.(부모노드명).append(변수명)
```
## 1. READ
자바스크립트에서 원시자료형 변수의 값을 조회하기위해서는 변수의 이름, 참조 자료형인 배열에서는 index, 객체는 key를 이용해 값을 조회했던 것처럼.   
DOM에서 HTML 엘리먼트의 정보를 조회하기 위해선 querySelector의 첫 번째 인자로 셀렉터(selector)를 전달하여 확인해야 한다.

### querySelector란?   
주로 세가지가 가장 많이 쓰인다.
1. HTML 요소 ("div")   
2. id ("#tweetList")   
3. class  (.tweet)    
>셀렉터를 조회한다는 의미를 가지고 있다.   
query의 의미가 "질문하다"라는 것을 알고 있다면 역할을 쉽게 유추하실 수 있다.   
이 query라는 단어는 개발자 간에 "ㅇㅇㅇ를 조회한다"라는 의미를 "쿼리를 날리다"라는 jargon(특정 영역에서만 사용되는 단어)로 굳어져있다.

[예시코드]
```js
>> const (변수명) = document.querySelector(인자명)
//querySelector 에 '.tweet' 을 첫 번째 인자로 넣으면, 클래스 이름이 tweet 인 HTML 엘리먼트 중 첫 번째 엘리먼트를 조회할 수 있다.
const oneTweet = document.querySelector('.tweet')

//HTML 문서에는 클래스 이름이 tweet 인 요소가 여러 개 있는 데, 변수 oneTweet 에 할당된 요소는 단 하나다. 
//여러 개의 요소를 한 번에 가져오기 위해서는, querySelectorAll 을 사용한다.
//querySelectorAll로 클래스 이름이 tweet 인 모든 HTML 요소를 유사 배열로 받아온다.
const tweets = document.querySelectorAll('.tweet')

//이렇게 조회한 HTML 요소들은 배열처럼 for문을 사용할 수 있다.
```
* '배열 아닌 배열'을 유사 배열, 배열형 객체 등 다양한 이름으로 부른다. 
  정식 명칭은 Array-like Object 이다. Array-like Object 같이 개념을 설명하는 용어는 영어로도 명확하게 기억해두는 게 좋다.

* get으로 시작하는 DOM 조회 메서드를 볼 수도 있다. 이런 메서드는 querySelector 와 비슷한 역할을 하는 오래된 방식이다. 만약 이전 버전의 브라우저(인터넷 익스플로러) 호환성을 신경 써야 한다면, 이런 옛날 방식을 사용해야 할 수도 있다.


## 3. DELETE

## HTML Element를 삭제하는 방법
`1. 삭제하려는 요소의 위치를 알고 있는 경우에 사용하는 방법`

* remove 메서드를 사용
```js
const container = document.querySelector('#container')
const tweetDiv = document.createElement('div')
container.append(tweetDiv)
tweetDiv.remove() // 이렇게 append 했던 요소를 삭제할 수 있다.

```
* innerHTML : 모든 자식 요소 지우기
```js
document.querySelector('#container').innerHTML = '';
```

 

* removeChild : 자식 요소를 지정해서 삭제하는 메서드   
  (innerHTML의 보안문제점을 보완할 대체 방안)

  `모든 자식 요소를 삭제하기 위해, 반복문(while, for, etc.)을 활용할 수 있다.`
  
```js
const container = document.querySelector('#container');
while (container.firstChild) {
  container.removeChild(container.firstChild);
}
```
제목에 해당하는 H2 "Tweet List"까지 삭제하는것을 방지하기 위해   
자식 요소가 담고 있는 문자열을 비교해 "Tweet List"만 남기거나, 새로운 변수를 생성하고 Tweet List를 할당해뒀다가 반복문이 끝난 뒤에 새롭게 추가할 수도 있다.   
또는 자식 요소를 하나만 남기게 할 수도 있다.   
   
[자식요소 하나 남기기 예시 코드]
```js
const container = document.querySelector('#container');
while (container.children.length > 1) {
  container.removeChild(container.lastChild);
}
//container의 자식 요소가 1개만 남을 때까지, 마지막 자식 요소를 제거합니다.
```



#
DOM mdn https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction#dom_and_javascript
