# CSS 정리

### 1. 추천 라이브러리(팀협의)

- reset.css(https://meyerweb.com/eric/tools/css/reset/)
- normalize.css(https://necolas.github.io/normalize.css/)

- normalize 예제 (무조건 제일 위에)

```html
<link
  rel="stylesheet"
  href="https://necolas.github.io/normalize.css/8.0.1/normalize.css"
/>
```

### 2. 개선사항

- header.css 는 무조건 z-index: 999 이상
- header 영역이 margin의 오류로 padding 변경

```
margin-top의 오류라고 자주 발생(웹브라우저 문제)
이런 경우 padding-top 또는 테두리를 주어서 해결함
```

- header 영역이 스크롤시 `postion:fixed 되면서 높이가 반영안됨`

```
position:fixed 라고 세팅하면 높이값이 반영이 안됨
강제로 main 영역의 상단에 공간을 padding-top으로 적용 해결.
```

- 배너 슬라이드는 단방향임 즉, 무한루프가 아니라서 버튼 출력이 수정 필요

### 3. CSS 자동 정리 도구 활용

- 필수 사항은 아닙니다.
- https://h-owo-ld.tistory.com/184
- `PostCSS Sorting` 검색 및 설치

```json
"postcssSorting.config": {
    "order": [
      "custom-properties",
      "dollar-variables",
      "at-variables",
      {
        "type": "at-rule",
        "name": "extend"
      },
      {
        "type": "at-rule",
        "name": "include"
      },
      "declarations",
      {
        "type": "at-rule",
        "name": "media"
      },
      "rules"
    ],
    "properties-order": [
      "position",
      "top",
      "right",
      "bottom",
      "left",
      "z-index",

      "display",
      "flex",
      "flex-grow",
      "flex-shrink",
      "flex-basis",
      "flex-direction",
      "flex-wrap",
      "justify-content",
      "align-items",
      "align-content",
      "order",

      "float",
      "clear",
      "box-sizing",
      "width",
      "min-width",
      "max-width",
      "height",
      "min-height",
      "max-height",
      "margin",
      "padding",
      "overflow",
      "overflow-x",
      "overflow-y",

      "font",
      "font-family",
      "font-size",
      "font-weight",
      "line-height",
      "letter-spacing",
      "text-align",
      "text-decoration",
      "text-transform",
      "color",

      "background",
      "background-color",
      "background-image",
      "background-size",
      "background-position",
      "background-repeat",

      "border",
      "border-width",
      "border-style",
      "border-color",
      "border-radius",

      "box-shadow",
      "opacity",
      "transition",
      "transform",

      "cursor",
      "visibility",
      "content"
    ],
    "unspecified-properties-position": "bottom"
  }
```

- 단축키 설정하기 : 설정 > Keyboard Shortcuts 선택
