# REST API

- REST API란 HTTP요청을 보낼 때 어떤 URI애 어떤 메소드를 사용할건지 지키는 약속을 말한다.

- 요청의 목적이 어떤 동작이나 정보인지 요청 자체의 모습으로 알 수 있다.   
  restful하게 요청을 만들면 정보에 대한 이해도가 직관적이므로 협업을 수월하게 할 수 있다.

- REST API는 HTTP 디자인을 따르며 요청을 보낼시 CRUD에 따른 메소드를 맞춰 사용한다.  
  
- REST API는 각각 목적에 맞는 CRUD메소드와 이에 사용될 정보를 담은 바디로 이루어져 있다.

- 클라이언트와 서버가 데이터를 주고받는 형태로 JSON, XML, TEXT, RSS 등이 있다.
   
****
## 📌REST API의 구성 요소

### 🧩 리소스 (자원)
- 모든 자원에는 고유한 ID가 존재하고, 이 자원은 서버에 존재한다.
- 자원을 구별하는 ID는 '/students/:student_id'와 같은 URI이다.
- Client는 URI를 이용해 자원을 지정하고, 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.

### 🧩 메소드 (CRUD)

- HTTP 프로토콜은 CRUD에 따른 메소드를 사용한다.
- HTTP 프로토콜은 GET, POST, PUT, PATCH, DELETE의 메소드를 제공한다.

  [CRUD에 따른 메서드]
![img](https://user-images.githubusercontent.com/104320234/178094258-05490483-b77e-460a-849d-ac740a42a9a7.png)

    - GET : 정보 요청, URI가 가진 정보를 검색하기 위해 서버에 요청한다.(READ)
    - POST : 정보 입력, 클라이언트에서 서버로 전달하려는 정보를 보낸다. (CREATE)
    - PUT : 정보 업데이트, 정보 전체를 교체할 때 사용한다. (UPDATE)
    - PATCH : 정보 업데이트, 정보 일부를 수정할 때 사용한다. (UPDATE)
    - DELETE : 정보 삭제 (DELETE)

>put은 정보를 통채로 교체할때, patch는 정보중 일부를 특정방식으로 변경할때 사용한다.

****
## 📌REST API의 사용규칙

1. URI는 각 요청의 의도를 쉽게 파악할 수 있도록 목적에 따라 구분해 restful하게 작성해야 한다.
    - URI는 동사가 아닌 명사로 이루어져야 한다.
    - 소문자를 사용한다.
2. 자원에 대한 행위는 HTTP 메소드로 표현한다.
    - URI에 메소드가 들어가면 안된다.
    - 행위에 대해 동사로 쓰면 안된다.
3. 슬래시로 계층관계를 나타낸다.
4. URI의 마지막 문자로 슬래시를 넣지 않는다.
5. 밑줄 _ 은 URI에 사용하지 않는다.
6. 파일 확장자는 URI에 넣지 않는다.

[엔드 포인트 작성법]
1. 동사, HTTP 메서드, 혹은 어떤 행위에 대한 단어 사용은 지양하고,   
   **리소스**에 집중해 명사 형태의 단어로 작성하는 것이 바람직한 방법이다. 
2. 요청에 따른 응답으로 리소스를 전달할 때에도 사용한 리소스에 대한 정보와 함께 리소스 사용에 대한 성공/실패 여부를 반환해야한다.
3. 만약 실패 시 리소스 사용에 대한 실패 여부를 포함한 응답을 받아야 한다.


****

## 📌 REST API 성숙도 모델

![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/9u2YISpdpWnz1JLxYbrF2-1634092735361.png)

>REST 성숙도 모델은 총 4단계(0~3단계)로 나누어진다.  
실제로 엄밀하게 3단계까지 지키기 어렵기 때문에 2단계까지만 적용해도 좋은 API 디자인이라고 볼 수 있고, 이런 경우도 HTTP API 라고도 부른다.

## 🧩 REST API 성숙도 모델 - 0단계
![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/LhV1GyLYcpniAk6X4kgd9-1634092764533.png)

0단계에서는 단순히 HTTP 프로토콜을 사용하기만 한다.   
하나의 엔드포인트만 사용해서 HTTP 메소드도 POST만 사용한다.   
하나의 메소드가 여러개의 매개변수를 통해서 다른 동작을 하게 된다.   
0단계는 REST API라고 할 수 없으며 REST API를 작성하기 위한 기본 단계하고 볼 수 있다.

## 🧩 REST API 성숙도 모델 - 1단계
![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/w2tEUwx7YSe8J-odREuH7-1634092794088.png)
1단계에서는 개별 리소스(Resource)와의 통신을 준수해야 하며, 모든 자원은 개별 리소스에 맞는 엔드포인트(Endpoint)를 사용해야한다.  
요청하고 받는 자원에 대한 정보를 응답으로 전달해야 한다.

## 🧩 REST API 성숙도 모델 - 2단계
![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/zbLOnJr3QGE7mPsJQuU2l-1634092891925.png)
REST 성숙도 모델 2단계에서는 **CRUD(Create, Read, Update, Delete)**에 맞게 적절한 HTTP 메서드를 사용하는 것에 중점을 둔다.  
ex) 조회(Read)가 필요할때는 `GET`메서드를 사용해서 요청. `GET`
메서드는 `body`를 가지지 않기 때문에 query parameter를 사용하여 필요한 리소스를 전달. 

생성(Create)을 해야할때는 `POST`메서드를 사용하여 요청 해야하며 또한 적절한 메서드 요청 후 받는 응답의 반환도 중요하다. 예를들어  `POST`메서드로(생성) 요청시  응답은 새롭게 생성된 리소스를 보내주기 때문에`201 Created`로 명확하게 작성 하여 응답해야 한다.

관련 리소스를 클라이언트가 `Location`헤더에 작성된 URI를 통해 확인할 수 있도록 하면 완벽하게 REST 성숙도 모델의 2단계를 충족한 것이라고 볼 수 있다.

## 🧩 REST API 성숙도 모델 - 3단계
![img](https://s3.ap-northeast-2.amazonaws.com/urclass-images/-tPoMXplx9rnuecicTn1F-1634092918044.png)
마지막 3단계는 HATEOAS(Hypertext As The Engine Of Application State) 라는 약어로 표현되는 하이퍼미디어 컨트롤이 적용된다. 3단계의 요청은 2단계와 동일하지만, 응답에 리소스의 URI를 포함한 링크(하이퍼미디어 컨트롤을 포함함)요소를 넣어 새로운 기능에 접근할 수 있도록 하는 것이 3단계의 핵심 포인트이다.


## 🧩 Open API

예시로 정부에서 제공하는 공공데이터가 있다. 
공공데이터에 쉽게 접근할 수 있도록 정부는 Open API의 형태로 공공데이터를 제공하고 있다. 
공공데이터 포털에 접속해 원하는 키워드를 검색하면, 해당 키워드와 관련된 API를 확인할 수 있다.

이 API에는 "Open"이라는 키워드가 붙어 있으며 글자 그대로 누구에게나 열려있는 API이다. 
그러나 "무제한으로 이용할 수 있다"라는 의미는 아니다. 
API마다 정해진 이용 수칙이 있고, 그 이용 수칙에 따라 제한사항(가격, 정보의 제한 등)이 있을 수 있다.

## 🧩 API Key

API를 이용하기 위해서는 **API Key**가 필요하며 API key는 서버의 문을 여는 열쇠이다. (가끔 API key가 필요하지 않은 경우도 있다.)

API Key가 필요한 경우에는 로그인한 이용자에게 자원에 접근할 수 있는 권한을 API Key의 형태로 제공하고, 데이터를 요청할 때 API key를 같이 전달해야 원하는 응답을 받을 수 있다.
****


# JSON  (JavaScript Object Notation)

JSON은 JavaScript Object Notation의 약자이다.   
통신방법도 프로그램도 아닌 데이터를 표현하는 표현 방법이다.

JSON은 사람이 읽을 수 있는 텍스트 기반의 데이터 교환 표준으로
XML의 대안으로서 좀 더 쉽게 데이터를 교환하고 저장하기 위하여 고안되었다.

JSON은 텍스트 기반이므로 어떠한 프로그래밍 언어에서도 JSON 데이터를 읽고 사용할 수 있다.

데이터를 받아서 객체나 변수로 할당하기 위해 사용한다.

## 📌 JSON 데이터 유형

JSON은 여러 데이터 유형으로 세분화할 수 있다.

1. 문자열: 백슬래시(\) 이스케이프 문자를 사용
2. 숫자: 자바스크립트의 배정도수 부동소수점 형식을 따른다.
3. Boolean: 따옴표로 묶이지 않으며 문자열 값으로 취급
4. Null: 키에 어떤 값도 할당되어 있지 않은 경우
5. 객체: {}(중괄호) 사이에 삽입된 한 쌍의 이름 또는 값. 키는 문자열이어야 하며 쉼표로 구분
6. 배열: 순서가 지정된 값의 모음이다. JSON에서 배열 값은 문자열, 숫자, 객체, 배열, Boolean, Null 유형이어야 한다.

## 📌JSON 특징

1. JSON은 자바스크립트를 확장하여 만들어졌다.

2. 자바스크립트 객체 표기법을 따른다.
   
3. 자바스크립트를 이용하여 JSON 형식의 문서를 쉽게 자바스크립트 객체로 변환할 수 있는 이점이 있다.
   
4. 속성-값 쌍으로 이루어져 있다.

5. 서버와 클라이언트간의 교류에서 일반적으로 사용된다.

6. JSON은 자바스크립트 구문 형식이긴 하지만 특정 프로그래밍 언어와 운영체제에 속하지않고 독립적이다.

7. 대부분의 프로그래밍 언어에서 JSON 포맷의 데이터를 핸들링 할 수 있는 라이브러리를 제공한다.  

## 📌 JSON 사용법


### 1. JSON.stringify() 객체를 문자열로 변환
```js
const json = {"test" : "value"}

const data = JSON.stringify(json);

//console.log(data);
```

### 2. JSON.parse() 문자열을 객체로 변환   
JSON.parse() 사용 시 주의할 점은 해당 문자열이 반드시 JSON형식이어야 된다.
```js
const str = '{"test" : "value"}';

const parsingData = JSON.parse(str);

//console.log(parsingData);
```

### 3. 데이터 추가 삭제법

```js
let uers = {
    user1: "sy", 
    user2: "ke", 
    user3: "kh"};

//Json 오브젝트 추가
//오브젝트.ID = VALUE;
user.user4 = 'yk';

//JSON오브젝트 삭제
delete json.sy;
console.log(users); //{user2: "ke", user3: "kh", user4: "yk"}
```

## 📌 주의할 점

AJAX를 사용해 데이터를 주고받을때 JSON은 자바스크립트 그 자체도 전달할 수 있다.   
따라서 JSON데이터를 받았는데 단순 데이터가 아닌 자바스크립트일 경우 그게 실행될 수 있다.  
이 점을 방지하기 위해 받은 내용에서 순수한 데이터만을 추출하기 위한 JSON관련 라이브러리를 따로 사용한다.
