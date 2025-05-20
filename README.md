# JS

- JS는 두 가지로 크게 분류
- Node와 Web(웹브라우저)로 분류

### JS코딩 좋은 위치

- 가장 좋은 자리는 html이 완료되는 시점

```js
// html 의  document 가 모두 로드 되면 실행하기
// html 의  이미지, 파일 등등 리소스가 준비되면 실행
// 표준입니다.
window.addEventListener("load", function () {});

// html 만 로드 완료를 체크합니다.
window.addEventListener("DOMContentLoaded", function () {});
```

### 요소(Element) 선택법

```js
// DOM만 완성하면 됨, 기준으로 코드 진행
window.addEventListener("DOMContentLoaded", function () {
  console.log("gdgdgdgdgd");
  // 우리가 원하는 요소(Element)를 선택하는 법
  // - Tag를 선택하고싶을 때 (Tag Element)
  this.document.getElementsByTagName("header");
  this.document.getElementsByClassName("header");
  // - CSS 선택자를 이용해서 선택하고 싶을 때 (CSS Element)
  this.document.querySelector(".header");
  this.document.querySelectorAll(".header");
  // - ID 선택자를 이용해서 선택하고 싶을 때 (ID Element)
  this.document.getElementById("header");
});
```

### 다양한 이벤트의 이해

- 웹브라우저가 체크하는 변화를 `이벤트` 라고 함
- 이벤트 작성법 3가지

##### 1. 태그에 직접 이벤트 작성하기

```js
<태그 on이벤트="코드"></태그>
<header class="header" onclick="alert('안녕')"></header>
```

##### 2. 요소에 속성으로 이벤트 작성하기

```js
요소.on이벤트 = function () {};

const header = this.document.querySelector(".header");
header.onclick = function () {
  alert("반가워");
};
```

##### 3. 요소에 이벤트 핸들러로 이벤트 작성하기

```js
요소.addEventListener("이벤트", function () {});

const header = this.document.querySelector(".header");
header.addEventListener("click", function () {
  alert("표준 반가워");
});
```

##### 4. 활용빈도가 높은 `윈도우 이벤트`

- `load` :
- `DOMContentLoaded` :
- `resize` : 웹브라우저 너비, 높이 변경시 발생
- `scroll` : 웹브라우저에서 스크롤이 일어나면 발생

##### 5. 활용빈도가 높은 `마우스 이벤트`

- `click` : 마우스 왼쪽 클릭
- `mouseenter` : 마우스 커서가 요소에 걸쳐지면
- `mouseleave` : 마우스 커서가 요소에서 벗어나면

##### 6. 활용빈도가 높은 `키보드 이벤트`

- `keyup` : 키보드에서 키 입력 후 이벤트 발생
- `keydown` : 키보드에서 키 입력 시 이벤트 발생
- `keypress` : 키보드에서 키 누르고 있으면 이벤트 발생

##### 7. 활용빈도가 높은 Form 관련 이벤트 (추후 정리)

### CSS 제어법

##### 1. inline 형태로 적용하기 (가끔 활용)

- `대상.style.css속성 = "값"`

```js
// DOM 만 완성화면 됩니다. 기준으로 코드를 진행함.
// DOM은 html 태그 구조를 말함 (Document Object Model) : 객체
// 아래 문장은 html 이 완성되어졌으면 실행
window.addEventListener("DOMContentLoaded", function () {
  // 아래 구문은 header 변수를 만들고 html (document)에서 css 선택자로 값을 세팅
  const header = this.document.querySelector(".header");
  const logo = this.document.querySelector(".logo");
  const search = this.document.querySelector(".search");
  const member = this.document.querySelector(".header_top_right");
  const eventMenu = this.document.querySelector(".header_bottom_eventmenu");

  // 윈도우에 스크롤(scroll 이벤트)이 일어나면 기능을 작동시킴
  this.window.addEventListener("scroll", function () {
    // 스크롤이 되었을 때 스크롤바의 Y축의 상단 픽셀위치값
    const scrollY = window.scrollY;
    // headerTop 영역의 높이값을 px로 알고싶다
    const headerTopH = this.document.querySelector(".header_top");
    console.log(headerTopH.offsetHeight); // 50px 출력

    // 만약 50보다 작으면 전체를 보이고, 그렇지 않으면 일부분을 숨김
    if (scrollY <= headerTopH.offsetHeight) {
      // console.log("모두 보여라");
      logo.style.display = "block";
      eventMenu.style.display = "block";
    } else {
      // console.log("일부만 보여라");
      // 로고를 css로 제어하고 싶다
      logo.style.display = "none";
      eventMenu.style.display = "none";
      search.style.position = "absolute";
      search.style.left = "350px";
      search.style.top = "48px";
    }
  });
});
```

##### 2. css 클래스 활용하기 (자주 활용)

- `대상.classlist.add("클래스명")`
- `대상.classlist.remove("클래스명")`
- `대상.classlist.toggle("클래스명")`
- `대상.classlist.contain("클래스명")`

### 슬라이드 외부 라이브러리 활용하기

- 직접 만들지 않기를 권장함
- `Swiper` : 매우 추천 (https://swiperjs.com/)
- `slick` : 추천 (https://kenwheeler.github.io/slick/)
- `bxSlide` : 비추천 (https://bxslider.com/)
