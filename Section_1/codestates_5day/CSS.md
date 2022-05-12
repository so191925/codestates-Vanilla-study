## ✉️ 학습목표

> ### Chapter1. CSS 기초
> - CSS의 사용 목적을 이해한다.
> - CSS의 기본 문법과 구조를 이해한다.
> - CSS를 HTML에 적용하는 방법에 대해서 이해한다.
> - HTML 안에 CSS를 직접 정의하는 것을 권장하지 않는 이유를 이해한다.
> - CSS를 이용해 텍스트를 꾸밀 수 있다.
> - CSS에서 쓰이는 단위를 기억하고, 각 단위가 적합한 경우를 구분할 수 있다.
> - MDN 또는 w3school 등의 레퍼런스 사이트를 이용해 CSS 속성을 검색하고 이용할 수 있다.

> ### Chapter2. 박스모델
> - CSS 박스 모델을 이해할 수 있다.
> - 박스를 구성하는 네 가지 요소를 구분하고 각각에 대해 설명할 수 있다.
> - margin, boder, padding, content
> - 박스 크기를 측정하는 두 가지 기준의 차이를 이해할 수 있다.

> ### Chapter3. CSS selector
> - 다양한 CSS selector 규칙을 이해한다.
> - 후손 selector와 자식 selector의 차이를 이해한다.
> - 필요시 검색을 통해 필요한 selector를 찾아 적용할 수 있다.

## CSS란?
웹 페이지 스타일 및 레이아웃을 정의하는 스타일시트 언어이며 사용자에게 더 나은 UI, UX를 제공할 수 있다.

- UI (User Interface) : 사용자와 시스템 사이에서 의사소통 할 수 있도록 하는 매개체이다.
- UX (User Experience) : 사용자가 경험하고 느낀점의 총제적 경험이다.

### 🧩 HTML에 CSS 파일 삽입 방법
외부 CSS파일을 설정하려면 link 태그를 사용한다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Modern CSS</title>
  <!-- CSS 파일 추가 href의 상태 값으로는 파일의 절대경로나 상대경로를 입력한다. -->
  <link rel="stylesheet" href="index.css" />
</head>
<body>
    <!-- 화면을 구조를 잡는 공간 -->
</body>
</html>
```

### 🧩 CSS의 기본 문법

- 셀렉터 : 요소 이름이나 id, 또는 클래스를 선택한다.
- 선언 블록 : 중괄호로 요소에 적용할 내용을 작성한다.
- 속성명과 속성값 : 속성에 적용할 주제와 내용을 작성하여 적용한다.
- 선언구분자 : 속성과 값의 끝에 `;` (세미콜론)을 붙혀서 속성을 구분한다.

<p align="center">
  <img src="../img/css-content.png" alt="html" width="500px" height="300px"/>
</p>

### 🧩 셀렉터 id와 class의 차이점

1) id 
- `#`으로 요소를 선택한다.
- 한 html 파일에 하나의 요소만 적용이 가능하다.
- 특정 요소에 이름을 붙히는 역할을 하며 중복되지 않는다.

2) class
- `.`으로 요소를 선택한다.
- 동일한 값의 갖는 요소를 지정할 수 있다.
- 스타일 분류에 사용된다. (같은 CSS를 일괄지정)

## 글자 CSS

### 🧩  색상 변경하기
속성에 삽입할 수 있는 값으로는 HEX 코드와 주요 색상의 이름을 사용할 수 있다.

```css
p {
  /* HEX 코드 */
  color: #ff0000;
  /* 주요 색상의 이름 */
  background-color: red;
}
```

- `color` 속성으로 글자의 색상을 변경한다.
- `background-color` 속성으로 배경 색상을 변경한다.
- `border-color` 속성으로 박스 테두리 색상을 변경한다.

### 🧩 background-color와 background의 차이

- `background-color`는 배경의 색상만 지정할 수 있다.
- `background`는 다른 옵션도 지정할 수 있으며 다양한 background의 축약 속성이다.
- 만약 배경 색만 바꿀 의도라면 시멘틱에 맞게 `background-color`를 사용하는게 좋아보인다.

### 🧩 글꼴 변경하기
`font-family`를 사용한다.

- 사용하려는 글꼴이 존재하지 않을 수도 있다.
- 디바이스에 따라 지원하지 않을 수도 있다.
- 웹 폰트 기술을 사용하면 문제가 해결된다.
- [구글폰트](https://fonts.google.com/)는 다양한 무료 글꼴을 제공해준다.

### 🧩 글자 스타일링

- 크기 : `font-size`
- 굵기 : `font-weight`
- 밑줄, 가로줄 : `text-decoration`
- 자간 : `letter-spacing`
- 행간 : `line-height`

### 🧩 글자 정렬

- 가로 정렬 : `text-align`
- 세로 정렬 : `vertical-align` 부모의 `display` 속성의 값이 `table-cell`일 때만 가능

## CSS 크기 단위
크기의 단위는 절대 단위와 상대 단위가 있다.

- 절대 단위: px, pt 등
- 상대 단위: %, em, rem, ch, vw, vh 등

### 🧩 em과 rem의 차이

- em : 부모의 엘리먼트에 따라서 상대적으로 크기가 변경된다.
- rem : 루트의 글자 크기에 종속받는다.

## 박스 모델
모든 컨텐츠는 각자의 영역을 가지며 하나의 콘텐츠로 묶이는 요소들이 하나의 박스 모델이라고 지칭하며 항상 직사각형 모양이다.

### block 모델과 inline 모델
박스 모델의 종류를 줄 바꿈이 되는 모델과 줄 바꿈이 되지 않는 모델로 크게 2가지로 구분한다.

- block 모델 : 줄 바꿈이 되는 모델이며 대표적으로 `<div>`태그가 있다. (width, height로 크기를 조절 가능하다.)
- inline 모델 : 줄 바꿈이 되지 않는 모델이며 대표적으로 `<span>`태그가 있다. (width, height로 크기를 조절 불가능하다.)

### inline-block 모델
inline 모델은 요소들의 크기에 비례해 공간을 차지하는 특성이 있어서 크기가 조절이 불가능하지만 inline-block 모델은 inline의 줄 바꿈이 되지않는 특성을 유지하면서 박스의 크기를 조절할 수 있다.

## 박스를 구성하는 요소

- margin (바깥 여백) : 박스 모델의 바깥 여백을 나타낸다.
- border (테두리) : 박스 모델의 테두리를 나타낸다.
- padding (안쪽 여백) : 박스 모델과 안쪽 요소들의 여백을 나타낸다.
- content : 박스를 구성하는 자식 태그들의 요소를 나타낸다.

<p align="center">
  <img src="../img/box-model.png" alt="html" width="500px" height="300px"/>
</p>

### 🧩 박스 요소 사용법

- border

```css
p {
  /* 테두리 두께, 테두리의 종류, 테두리의 색깔 순으로 입력한다. */
  border: 1px solid red;
}
```

- margin

```css
p {
  /* 위 오른쪽 아래 왼쪽 순으로 시계 방향으로 진행된다. */
  margin: 10px 20px 30px 40px;
}
```

```css
p {
  /* (위, 아래) (오른쪽, 왼쪽)을 한번에 지정한다.*/
  margin: 10px 20px;
}
```

```css
p {
  /* 전부다 똑같은 크기로 지정한다. */
  margin: 10px;
}
```

- padding (margin과 사용법이 동일하다.)

```css
p {
  /* 위 오른쪽 아래 왼쪽 순으로 시계 방향으로 진행된다. */
  padding: 10px 20px 30px 40px;
}
```

```css
p {
  /* (위, 아래) (오른쪽, 왼쪽)을 한번에 지정한다.*/
  padding: 10px 20px;
}
```

```css
p {
  /* 전부다 똑같은 크기로 지정한다. */
  padding: 10px;
}
```

### 🧩 overflow 속성
박스의 바깥으로 나간 자식요소들의 상태를 지정할 수 있는 속성이다.

```css
/* 자식요소가 넘치는 경우 스크롤 생성 */
  overflow: auto;
}
```

### 🧩 박스 모델의 크기 측정
박스 모델의 크기는 margin을 제외한 박스 모델의 요소의 전체 합이다.

```css
#container {
  /*
  width의 값은 왼쪽 오른쪽 padding 10 10 왼쪽 오른쪽 border 2 2의 값을 모두 합친 크기이다.
  */
  width: 300px;
  padding: 10px;
  background-color: yellow;
  border: 2px solid red;
}
```

### 🧩 content-box와 border-box의 차이점

- content-box : 실제 차지하는 너비를 기준으로 width + padding + border의 값으로 측정한다.
- border-box : width의 넓이를 padding과 border를 합친 값으로 설정한다. 레이아웃의 크기를 width만 생각하면 되므로 권장하는 방법이다.

<p align="center">
  <img src="../img/border-box.png" alt="html" width="500px" height="300px"/>
</p>

## CSS Selector
CSS Selector란 CSS를 적용하고 싶은 태그에 접근하는 방법을 제시한다.

### 🧩 셀렉터의 종류

- 전체 셀렉터 : 문서의 모든 요소를 선택한다.

```css
* { }
```

- 태그 셀렉터 : 같은 태그명을 가진 요소들은 선택한다.

```css
h1 { }
span { }
```

- ID 셀렉터 : 요소의 속성 id로 접근하며 `#`를 붙혀준다.

```css
#container { }
```

- Class 셀렉터 : 요소의 속성 class로 접근하며 `.`을 붙혀준다.

```css
.btn { }
```

- Attribute 셀렉터 : 속성 값의 조건에 따라 요소를 선택한다.

```css
  a[href] { }
  p[id="only"] { }
  p[class~="out"] { }
  p[class|="out"] { }
  section[id^="sect"] { }
  div[class$="2"] { }
  div[class*="w"] { }
```

- 자식 셀렉터 : 첫 번째 입력한 바로 아래의 자식의 요소를 선택한다.
```css
header > p { }
```

```html
<header>
	<p> <!-- 선택 -->
		<span>
			<p></p>
		</span>
	</p>
	<p> <!-- 선택 -->
		<span>
			<p></p>
		</span>
	</p>
</header>
```
- 후손 셀렉터 :첫 번째로 입력한 바로 아래의 후손의 요소를 선택한다.
```css
header p { }
```

```html
<header>
	<p><!-- 선택 -->
		<span>
			<p><!-- !!선택!! -->
			</p>
		</span>
	</p>
	<p><!-- 선택 -->
		<span>
			<p><!-- !!선택!! -->
			</p>
		</span>
	</p>
</header>
```

- 형제 셀렉터 : 같은 부모이며 첫 번째 입력한 요소와 같은 레벨에 있는 두 번째 요소를 모두 선택한다.

```css
section ~ p { }
```

```html
<header>
	<section></section>
	<p></p> <!-- 선택 -->
	<p></p> <!-- 선택 -->
	<p></p> <!-- 선택 -->
</header>
```

- 인접 형제 셀렉터 : 같은 부모이며 첫 번째 입력한 요소와 같은 레벨에 있는 두 번째 요소를 하나만 선택한다.

```css
section + p { }
```

```html
<header>
	<section></section>
	<p></p> <!-- 선택 -->
	<p></p>
	<p></p>
</header>
```

- 가상 클래스 셀렉터 : 가상 클래스는 요소의 상태 정보에 기반해 요소를 선택합니다.

```css
a:link { } /*사용자가 방문하지 않은 <a>요소를 선택합니다.*/
a:visited { } /*사용자가 방문한 <a>요소를 선택합니다. */
a:hover { } /* 마우스를 요소 위에 올렸을 때 선택합니다. */
a:active { } /* 활성화 된(클릭된) 상태일 때 선택합니다. */
a:focus { } /* 포커스가 들어와 있을 때 선택합니다. */
```

- UI 요소 상태 셀렉터

```css
input:checked + span { } /*체크 상태일 때 선택합니다. */
input:enabled + span { } /*사용 가능한 상태일 때 선택합니다. */
input:disabled + span { } /*사용 불가능한 상태일 때 선택합니다. */
```

- 구조 가상 클래스 셀렉터

```css
p:first-child { }
ul > li:last-child { }
ul > li:nth-child(2n) { }
section > p:nth-child(2n+1) { }
ul > li:first-child { }
li:last-child { }
div > div:nth-child(4) { }
div:nth-last-child(2) { }
section > p:nth-last-child(2n + 1) { }
p:first-of-type { }
div:last-of-type { }
ul:nth-of-type(2) { }
p:nth-last-of-type(1) { }
```

- 부정 셀렉터

```css
input:not([type="password"]) { }
div:not(:nth-of-type(2)) { }
```

- 정합성 확인 셀렉터

```css
input[type="text"]:valid { }
input[type="text"]:invalid { }
```