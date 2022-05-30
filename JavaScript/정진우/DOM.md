# DOM

# 📌 **Document Object Model** 문서 객체 모델

- DOM이란 브라우저가 HTML 웹 페이지를 인식하는 방식을 계층화시켜 트리구조로 만듣 객체 모델이다.
- 웹 문서의 모든 요소를 자바스크립트를 이용하여 조작할 수 있도록 객체를 사용하여 문서를 해석하는 방법을 말한다.
- DOM이 있는 핵심적인 이유는 HTML/CSS를 프로그래밍적으로 조작하기 위해서 입니다.

  ![Alt text](https://velog.velcdn.com/images%2Fsolmii%2Fpost%2Fb9b74817-bebb-4f8f-8e7e-cd0ae796761d%2Fimage.png)

- tree에서는 위쪽의 노드를 **_부모(parent) 노드_**, 아래쪽 노드를 **_자식(child) 노드_** 라고 한다. root node는 가장 위에서 시작되는 node이니까 **_parent(부모)가 없는 node_** 가 되고, 이를 **_뿌리(root) node_** 라고도 부른다.
  반대로, **_children(자식)이 없는 node_** 를 **_잎(leaf) node_** 라고도 한다.
  뿌리(root)에서 시작해서 잎(leaf)에서 끝나는 것!
- DOM의 트리구조는 이렇게 노드와 가지로 표현한다. 네모 상자가 노드이고 노드와 노드 사이를 연결하여 관계를 표시하고 있는 선이 가지이다. 위 그림에서 확인할 수 있듯이 노드는 웹 문서의 HTML 태그 요소만 표현하는 것이 아니다. 모든 텍스트와 이미지, 태그의 속성들까지 객체화하여 DOM트리에 표현한다.

# 📌 node란

- tree 구조에서 root 노드를 포함한 모든 개개의 개체를 node라고 표현한다.
  head, body, title, script, h1, HEADER-1 등의 태그뿐 아니라 태그 안의 텍스트나 속성 등도 모두 node에 속한다.

## 🧩 문서 노드(Document Node)

- 트리의 최상위에 존재하며, 하위 자식 노드에 접근하기 위해선 Document Node를 통해야만 한다. Dom 트리에 접근하기 위한 시작점이다.

## 🧩 요소 노드 (Element Node)

- 웹 문서의 태그는 Element Node로 표현된다. 모든 Element Node는 Attribute Node와 Text Node를 자식으로 가질 수 있는 데, 이 자식 노드들을 변경하여 웹 페이지를 동적으로 조작할 수 있다.

## 🧩 속성 노드 (Attribute Node)

- 태그의 모든 속성은 Attribute Node로 표현하며 해당 태그의 자식 노드로 인식된다.

## 🧩 텍스트 노드 (Text Node)

- 태그가 가지고 있는 텍스트는 해당 Element Node의 자식 노드인 Text Node로 표현된다. Text Node는 Dom 트리의 가장 아래쪽에 위치하여 자신의 자식 노드는 가질 수 없다.

## 🧩 주석 노드 (Comment Node)

- 주석은 Comment Node로 표현한다.

---

JavaScript는 이 model로 웹 페이지에 접근하고, 페이지를 수정할 수 있다.

![Alt text](https://velog.velcdn.com/images%2Fsolmii%2Fpost%2Fe5d89bc5-abba-4245-9fb8-389f34e7cbd1%2Fimage.png)

DOM은 HTML인 웹페이지와 자바스크립트를 서로 잇는 역할을 한다.

자바스크립트가 HTML에 접근할 수 있는 방법은 document라는 전역객체를 통해 접근 할 수 있다. Javacsript의 document 객체는 DOM 구조를 접근하는 관문이며, document 객체는 HTML문서를 나타낸다.

| 메서드                                        | 설명                                                                       |     |     |
| --------------------------------------------- | -------------------------------------------------------------------------- | --- | --- |
| document.getElementById("id명")               | 해당 id명을 가진 요소 하나를 반환                                          |
| document.quertSelector("선택자")              | 해당 선택자를 만족하는 요소 하나를 반환                                    |
| document.getElementsByClassName("class명")[i] | 해당 class명을 가진 요소들을 배열에 담아 인덱스에 맞는 요소를 반환         |
| document.getElementsByTagName("tag명")[i]     | 해당 tag명을 가진 요소들을 배열에 담아 인덱스에 맞는 요소를 반환           |
| document.quertSelectorAll("선택자")[i]        | 해당 선택자를 만족하는 모든 요소들을 배열에 담아 인덱스에 맞는 요소를 반환 |

---

DOM은 자바스크립트가 아니다. DOM은 웹 문서에서만 존재하는 것이고, 브라우저가 자바스크립트를 이용해서 조작할 수 있도록 제공해주는 하나의 요소이다. 자바스크립트로 DOM을 조작하는 것은 HTML 웹 문서 자체를 수정하는 것이 아니고 DOM을 조작하는것이다.

> ## 📌 웹페이지가 만들어지는 방법

먼저 DOM을 이해하기 위해서는 웹 페이지의 빌드과정을 알아야 한다.

> ## 🧩 Critical Rendering Path

브라우저가 서버에서 페이지에 대한 HTML 응답을 받으면 화면에 표시되기 전에 많은 단계를 거쳐야 하는데 **_웹 브라우저가 원본 HTML 문서를 읽어들인 후, 스타일을 입히고 대화형 페이지로 만들어 뷰 포트에 표시하기까지의 과정_** 을 Critical Rendering Path, CPR이라고 한다.

> ## 🧩 CRP의 6단계 과정

## 1. DOM 트리 구축

HTML파일 문서의 구조를 파악하고, 트리형태로 된 데이터 구조를 만든다.

## 2. CSSSOM 트리 구축

CSS을 구조화 된 데이터 형태로 생성한 것이다.

## 3. JavaScript 실행

세번째 단계로 정리했지만, 첫번 째 단계인 DOM 구성 중에 일어날 수 있다. 웹 브라우저는 CRP과정을 거치며 DOM Tree를 구성하는데 이때 `script` 또는 외부 `script` 참조 구문을 만나면, DOM Tree를 구성하던 작업이 중지되고 `script` 가 먼저 실행된다. 이러한 특성 때문에 JavaScript는 '파서 차단 리소스'로 분류되며, HTML 작성 시 `script` 는 각각 엘리먼트에 대한 정의가 모두 끝난 뒤 마지막에 작성하는것을 권장한다.

## 4. 렌더 트리 구축

1, 2, 3 과정을 끝마치고 나면 웹 브라우저는 Render Tree를 구성한다. DOM Tree, CSSOM Tree를 기반으로 Render Tree가 구성되며 실제 웹 브라우저에 표현되는 정보를 갖고있다. Render Tree가 갖는 특징이 있다면, 숨겨진 요소는 포함되지 않는다는 점이다. 예를 들어 display: none 속성을 갖는 엘리먼트는 Render Tree에 포함되지 않는다.

## 5. 레이아웃 생성

앞서 Render Tree까지 구성이 완료되었다면 웹 브라우저는 viewport를 설정한다.`head` 영역에 `meta` 를 통해 viewport의 크기를 정의할 수 있으며, 정의되지 않은 경우 viewport의 크기는 기본 980px로 지정된다. 통상 viewport값은 웹 브라우저를 사용하는 pc 모니터해상도에 따라 설정되도록 한다.

## 6. 페인팅

웹 브라우저는 CRP의 마지막으로 Paint단계를 거친다. Paint에서는 앞서 구성된 정보를 토대로, 웹 브라우저를 통해 실제 화면에 데이터를 표현한다. Paint단계에서 걸리는 시간은 CSS복잡도와 DOM크기에 따라 차이가 있다.
![Alt text](https://velog.velcdn.com/post-images%2Fsurim014%2F212f1a60-2cd6-11ea-8bff-7fa1b7360f0c%2Fimage.png)  
 위와 같이 CRP 과정은 6단계로 나누어져 있지만 대략 렌더 트리 구축을 기점으로 두 단계로 나눌 수 있다.

- **첫번째 단계** : 브라우저는 읽어들인 문서를 파싱하여 최종적으로 어떤 내용을 페이지에 렌더링할 지 결정한다. (이 단계를 거치면 렌더 트리가 생성이 된다.)
- **두번째 단계** : 브라우저는 해당 렌더링을 수행한다.

  ![Alt text](https://velog.velcdn.com/post-images%2Fsurim014%2F78564f80-2cd5-11ea-b5ba-13b53e7b23f0%2Fimage.png)

> ## 🧩 렌더 트리
>
> 렌더 트리란 웹 페이지에 표시될 HTML요소들과 이와 관련된 스타일 요소들로 구성된다. 브라우저는 렌더 트리를 생성하기 위해 아래와 같이 두 모델이 필요하다.

- DOM(Document Object Model) : HTML 요소들의 구조화된 표현
- CSSOM(Cascading Style Sheets Object Model) : 요소들과 연관된 스타일 정보의 구조화된 표현

**참고: https://yceffort.kr/2020/07/critical-rendering-path**
