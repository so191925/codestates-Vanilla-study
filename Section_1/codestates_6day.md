# 코드스테이츠 - 6 day

## ✉️ 학습목표

> ### Chapter1. 레이아웃
> - 레이아웃이 필요한 이유를 이해한다.
> - 레이아웃을 위한 HTML을 만들 수 있다.

> ### Chapter2. Flex
> - display: flex; 를 자식 요소가 아닌 부모 요소에 적용해야 함을 이해한다.
> - flex-direction 을 이용하여 요소를 정렬할 방향을 결정할 수 있다.
> - justify-content 와 align-items 를 이용하여 수평-수직 정렬을 결정할 수 있다.
> - flex-grow 를 이용하여 요소를 얼마나 늘릴 것인지 결정할 수 있다.
> - flex-basis 를 이용하여 요소의 기본 크기를 결정할 수 있다.
> - VScode의 레이아웃을 Flexbox를 이용하여 구현할 수 있다.

## 레이아웃
각 요소들을 목적에 맞게 배치하는 작업

### 🧩 와이어 프레임 (Wireframe)
와이어로 설계된 모양을 의미하며 도형으로 웹의 인터페이스를 시각적으로 나타낸 것으로 어떤 목적을 가진 프로그램인지 유추할 수 있도록 방향을 제시한다.

### 🧩 목업 (Mock-up)
웹이나 앱에서의 목업이란 실제 작품이 동작하는 모습과 동일하게 HTML문서로 작성하는 방법

## flex-box
박스를 유연하게 늘이거나 줄여 레이아웃을 잡는 방법

### 🧩 flex 박스로 지정하기
display: `flex`로 부모 박스 요소에 적용하여 자식 박스의 방향, 크기, 배치 등등을 결정하는 방법

- 기본 설정은 row이다.
- row (가로정렬)
- column (세로정렬)
- reverse 속성들은 순서를 뒤집는다.

```html
<style>
#container {
    display: flex;
}
</style>

<section>
   <div>1</div>
   <div>2</div>
   <div>3</div>         
</section>

```
### flex-wrap
하위 요소가 부모의 요소의 크기를 벗어나면 줄 넘김처리

- 기본 설정은 nowrap이다.
- wrap (줄넘김 처리)
- reverse 속성들은 순서를 뒤집는다.

## 아이템 정렬 (부모 요소 속성)
축의 방향 기준으로 아이템들을 정렬한다.

- Main Axis : 요소들이 정렬된 축
- Cross Axis : Main Axis에 수직하는 축

### 🧩 justify-content
Main Axis축을 기준으로 정렬합니다.

### 🧩 align-items
Cross Axis축을 기준으로 정렬합니다.

### 아이쳄 정렬 (자식 요소 속성)

### 🧩 flex-grow
박스요소의 여백부분을 기준으로 지정된 비율을 갖는다. (flex-basis로 지정된 영역은 제외)

### 🧩 flex-shrink
박스요소의 줄이기를 가능하게 하는지 여부

### 🧩 flex-basis
박스요소의 고정 넓이를 지정한다.

<!-- flex 박스를 지정할 때 2 detph 아이템 요소를 정렬하고 싶으면 정렬하고 싶은 대상 바로 부모요소에 display: flex로 플렉스 박스를 지정해주고 아이템정렬 속성을 사용해야한다. -->

🏆  Pair : 류지창님