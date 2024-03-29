# Button과 Anchor의 사용

button 태그와 anchor 태그 사용에서 혼란을 느껴 정리



## table of contents

1. [button](#button)
1. [anchor](#anchor)
1. [button과 anchor의 사용](#button과-anchor의-사용)
1. [참고](#참고)

---



## button

버튼은 사용자가 양식을 제출하거나, 팝업을 열거나, 동작을 실행 또는 취소 등 이벤트를 트리거할 때 사용하는 위젯으로 **엔터키**와 **스페이스바**로 동작되어야 한다.  



## anchor 

링크는 주로 참조자료를 제공하기 위해 사용하는 것으로 주로 타겟은 내부이거나 외부일 수 있으며, 엔터키로만 동작이 된다. 


## button과 anchor의 사용

**버튼의 종류와 마크업의 사례에 대해 학습** 내용 정리

### `<a>` 태그

- 다른 자원을 참조(링크) 할 때 사용

### `<input>` 태그

- 사용자의 입력을 받은 `form`을 서버측에 전송하거나 서버측으로부터 새로운 데이터를 받아서 현재 페이지를 갱신할 때 사용

### `<button>`

- 자원을 참조하지도 않고 `form` 을 전송하지도 않으나 사용자의 **클릭** 또는 **Enter 행위**를 이용해서 화면의 인터페이스를 조작하고자 할 때 사용 
- `a`, `input`과 달리 닫기 태그가 존재하며 인라인 요소(텍스트, 이미지) 따위를 자식 요소로 포함할 수 있음



## button의 마크업 사례

`<a>`, `<input>` 요소의 쓰임새에 대해서는 비교적 명확하게 이해하고 경우가 많지만 `<button>` 요소의 경우 좀 더 구체적으로 세 가지 쓰임을 가질 수 있는데 다음과 같다.

### 첫째

`<input type="submit">` 과 같이 button에  `submit` 속성값을 사용하여 `form`을 `submit` 하는 용도(기능)로 쓸 수 있음

```html
<button type="submit">button</button>
```



### 둘째
`form` 을 `submit` 하지 않고 자바스크립트에 완전히 의존해서 화면의 인터페이스를 조작하는 역할. `type="button"` 으로 선언

```html
<button type="button">button</button>
```

### 셋째
`form` 을 `reset`(초기화) 하는 기능 

```html
<button type="reset">초기화</button>
```


### 사례

`<button type="button">button</button>` 의 사례

```html
<button type="button">button</button>
```

- 숨은 레이어(도움말 따위)를 펼치거나 접는 기능으로써 흔히 '토글' 버튼이라고 부르는 것.
- 레이어 또는 브라우저를 닫는 기능으로써 흔히 '닫기' 버튼이라고 부르는 것.
- '이전, 다음' 과 같이 브라우저 히스토리 기능을 자바스크립트로 구현하려는 경우.

언급하신 버튼들의 종류들에 대한 마크업.



### 이외에도 다양한 버튼 종류들에 대한 마크업

- **취소** - `button type="reset"` 또는 `button type="button"` 으로 구현.
- **목록** - 목록 페이지 링크 이므로 `a` 요소로 구현.
- **수정** - 수정 페이지 링크 일때에는 `a` 요소로 구현. 현재 페이지에서 자바스크립트를 이용하여 숨은 서식을 드러내는 기능이라면 `button type="button"` 으로 구현.
- **삭제** - 서버측 스크립트에 따라서 다양한 방법으로 마크업 할 수 있으나 보통 URL 이동을 하기 때문에 `a` 요소로 처리함. URL 이동 없이 그냥 삭제가 된다면 상황에 따라 `input` 또는 `button` 모두 사용할 수 있음.
- **글쓰기** - 글쓰기 페이지로 이동하는 버튼이라면 `a` 요소로 구현. 글쓰기 페이지에서 작성된 글을 전송하는 버튼이라면 `input type="submit"` 으로 구현



## 참고

- [3탄 - 버튼과 링크 - 접근성 AOA11Y 유튜브](https://www.youtube.com/watch?v=dhsr2LGTA-s)
- [버튼의 올바른 마크업 - 웹 접근성 연구소 전문가 답변](https://www.wah.or.kr:444/Participation/consultingView.asp?cType=&seq=1079&page=1?cType=&FindTxt=&cMail=)
- [링크? 버튼? 어떻게 다를까? #4 Button 살펴보기 - 접근성 AOA11Y 유튜브](https://www.youtube.com/watch?v=z3MlZIlMjXk)