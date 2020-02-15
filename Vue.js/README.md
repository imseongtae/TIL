# Vue.js

Vue.js는 가볍고 단순한 구조를 가지고 있어서 기존의 프로젝트에도 쉽게 적용할 수 있다. 또한 재사용이 가능한 컴포넌트 기반이므로 이를 이용하거나 ES6를 이용할 수도 있다. 그리고 routing, vuex를 사용해 한 곳에서 애플리케이션 전체에서 사용하는 데이터를 효과적으로 관리할 수도 있다. 

또한, 양방향 데이터 바인딩을 이용해 UI와 데이터 모델간의 reactivity 기능을 만들 수 있다는 장점이 있다.

## Vue.js 들어가기전, 요즘 웹 개발 트렌드

요즘은 서버가 데이터만 내려주고, 화면에 대한 책임은 프론트에게 맡기는 식으로 패러다임이 바뀌었다. 이 때문에 백엔드는 통신량은 많아졌지만 개발량은 오히려 줄어들었다.

예전에는 실제 데이터는 변하는 게 없더라도 디자인이 변하는 경우로 인해 개발을 하는 경우가 종종 있었다. 지금은 디자인만 바뀔 경우 개발에 백엔드가 필요 없다. 가령, 장고는 api서버로만 기능하고, 뷰 같은 서버를 따로 띄워서 화면을 그리는 모든 책임과 역할을 맡긴다.

## Table of Contents

1. [뷰 인스턴스](#뷰-인스턴스)
1. [컴포넌트를 사용한 작성방법](#컴포넌트를-사용한-작성방법)
1. [선언적 렌더링](#선언적-렌더링)
1. [라이프 싸이클](#라이프-싸이클)
1. [뷰라우터](#뷰라우터)
1. [뷰 HTTP 통신](#뷰-HTTP-통신)
1. [뷰템플릿](#뷰템플릿)
   - [디렉티브](#디렉티브)
1. [뷰 컴포넌트 구성방법](#뷰-컴포넌트-구성방법)
1. [Vue CLI](#Vue-CLI)
1. [Vue CLI를 활용한 프로젝트 생성법](#Vue-CLI를-활용한-프로젝트-생성법)
1. 
1. 
1. [Reference Docs](#Reference-Docs)

---

## Vue.js 시작을 위한 script

```html
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```



## 뷰 인스턴스

1. new Vue() 생성자를 통해 뷰 인스턴스 생성
2. el 속성으로 뷰 인스턴스가 그려질 지점 지정!
3. data 속성에 key-value 형식의 데이터를 정의
4. `{{ }}`를 통해 화면에 뷰인스턴스의 데이터 속성 값과 연결 혹은 대체됨

```html
<div id="app">
  {{ message }} <!-- 4. 화면에 뷰인스턴스의 데이터를 연결 -->  
</div>
```

```javascript
new Vue({ // 1. new Vue() 생성자를 통해 뷰 인스턴스 생성
  el:'#app', // 2. el 속성으로 뷰 인스턴스가 그려질 지점 지정!
  data: {
    message: "Hello Vue.js!" // 3. data 속성에 key-value 형식의 데이터를 정의
  }
})
```

### 뷰 인스턴스 옵션 속성

#### el 속성

`el` 속성은 통해 뷰로 만든 화면이 그려지는 시작점을 의미하며, `el`속성에 의해 선택될 선택자는 `CSS 선택자 규칙`과 같다.

```html
<div class="selected-by-css">
  {{ message }}
</div>
```

```javascript
new Vue({
  el:'.selected-by-css'
})
```

**[⬆ back to top](#table-of-contents)**



## 컴포넌트를 사용한 작성방법

컴포넌트 시스템은 Vue의 중요한 개념인데, 조합하여 화면을 구성할 수 있는 블록을 의미한다. 컴포넌트는 작고 독립적이므로 재사용할 수 있기 때문에 대규모 애플리케이션을 구축할 수 있게 해준다.

<img src="https://user-images.githubusercontent.com/40027211/74282098-e4dc5480-4d62-11ea-836e-3d3a456fbe14.png" alt="components" style="zoom:67%;" />

컴포넌트를 통해 아래와 같은 이점을 얻을 수 있다.

1. 화면을 일괄적인 패턴으로 구조화하여 개발할 수 있음
2. 재사용이 편리함

Vue에서 컴포넌트는 **미리 정의된 옵션을 가진 Vue 인스턴스**이다. Vue에서 컴포넌트를 등록하는 방법은 간단하다.

```javascript
// todo-item 엘리먼트는 app안에 child으로  작성되어야 함
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})

var app = new Vue({el:'#app', data: {...}})
```

```html
<div id="app">
  <ol>
    <todo-item></todo-item>
  </ol>
</div>
```

### HTML 사용자 정의 태그 스펙

HTML 사용자 정의 태그 스펙은 `케밥 케이스`와 `모두 소문자`를 강제하는데, 뷰에서는 이를 따르지 않아도 되지만 가급적 지키는 게 좋다.

### 컴포넌트의 유효 범위

전역 컴포넌트와 지역 컴포넌트는 유효 범위가 다르다.  

#### 전역 컴포넌트 

전역 컴포넌트는 한 번 등록하면 어느 인스턴스에서나 사용할 수 있으며, Vue 생성자에서 `component()`를 호출해야 한다. 

```javascript
Vue.component('global-component', {
  template: '<div>전역 컴포넌트임</div>'
})
```

#### 지역 컴포넌트 

지역 컴포넌트는 새 인스턴스를 생성할 때 마다 등록해야 하며, 유효 범위는 지역 컴포넌트가 등록된 인스턴스를 벗어날 수 없다. 사용하기 위해선 인스턴스의 속성으로 `components`를 추가하고 등록할 컴포넌트의 이름과 내용을 정의하면 된다.

```javascript
new Vue({
  components: {
    'local-component' : {
      template: '<div>지역 컴포넌트입니다.</div>'
    }
  }
})
```

### 좋은 컴포넌트를 위한 FIRST 원칙 

1. **F**ocus(단일 책임 원칙): 하나의 컴포넌트는 하나의 책임만을 가진다.

2. **I**ndependent(독립적): 컴포넌트는 다른 컴포넌트와 독립적으로 작동할 수 있어야 한다.

3. Reusable(재사용): 컴포넌트는 재사용할 수 있어야 한다.

4. Small(작음): 컴포넌트는 작은 크기로 유지한다. 이를 통해 유지 보수의 복잡성을 낮춘다.

5. Testable(테스트 가능): 유닛 테스트가 가능하여야 한다.	
	- 유닛 테스트가 가능하다는 것은 하나의 컴포넌트가 가진 기능과 목적이 명확함을 의미

### 커플링(Coupling)

어떤 모듈을 변경할 때 다른 모듈의 변경이 요구된다면 **커플링(Coupling)이 존재**한다

[참고: OOD - 커플링이란 무엇이며, 어떻게 줄일 수 있을까?](https://vandbt.tistory.com/13)

**[⬆ back to top](#table-of-contents)**



## 선언적 렌더링

Vue.js는 간단한 템플릿 구문을 사용해 DOM에서 데이터를 선언적으로 렌더링(**Declarative Rendering**)할 수 있는 시스템이 있다.

### {{ }} - 콧수염 괄호

`{{}}`는 뷰 인스턴스의 데이터를 HTML 태그에 연결하는 가장 기본적인 텍스트 삽입 방식이다.  뷰 인스턴의 데이터를 HTML에서 표현하기 위해 사용한다. 

> double mustaches, mustache tag, 콧수염 괄호, 이중 중괄호

```html
<div id="app">
  {{ message }}
</div>
```

```javascript
var app = new Vue({
	el: '#app',
  data: {
    message: 'hello Vue! thx'
  }
})
```

위의 코드는  웹 페이지 상에서는 아래처럼 표현된다!

---

hello Vue! thx

---

`Vue 인스턴스`의 `data`속성이 바뀌면 뷰 반응성에 의해 자동으로 갱신되는데, 이를 막고 싶다면 아래의 코드처럼, div 태그의 속성으로 `v-once`를 사용한다. 

```html
<div id="app" v-once>
  {{ message }}
</div>
```

**[⬆ back to top](#table-of-contents)**



## 라이프 싸이클

<img src="https://user-images.githubusercontent.com/40027211/74282739-f96d1c80-4d63-11ea-917f-e230861bbd4a.PNG" alt="life-cycle" style="zoom:67%;" />

인스턴스의 상태에 따라 호출할 수 있는 속성들을 라이프 싸이클이라고 한다. 뷰의 라이프 싸이클에는 인스턴스의 생성, 변경, 소멸과 관련된 8개 속성이 있다.

> 라이프 싸이클은 애플리케이션이 가지는 생명 주기를 일컫는다.

- `created`에서는 DOM에 접근하면 안 된다. 화면이 만들어지지도 않았는데, 뿌리려고 하면 문제가 생긴다. 화면에 대한 접근이 되지 않음
- `created`, `mounted`가 라이프싸이클에서 가장 중요한 속성이다.
- 



**[⬆ back to top](#table-of-contents)**

## 뷰 컴포넌트 통신

뷰의 컴포넌트는 유효 범위가 독립적이므로 다른 컴포넌트의 값을 직접적으로 참조할 수가 없으므로 뷰에서 정의한 컴포넌트 간의 데이터 전달 방법을 따라야 한다. 

<img src="https://user-images.githubusercontent.com/40027211/74282095-e3ab2780-4d62-11ea-9298-15d7092180f2.png" alt="props-events" style="zoom:67%;" />



### 상위에서 하위 컴포넌트로 데이터 전달하는 법

```javascript
Vue.component('child-component', {
  props: ['props 속성이름']
});
```

```html
<child-component v-bind:props 속성이름="상위 컴포넌트의 data 속성"></child-component>
```

### 컴포넌트 간의 관계

컴포넌트를 등록함과 동시에 뷰 인스턴스가 상위 컴포넌트가 된다. 위의 코드를 예시로 들면, `<child-component>`는 생성함과 동시에 뷰 인스턴스의 하위 컴포넌트가 된다. 

### 하위에서 상위로 컴포넌트 이벤트 전달하기

하위에서 상위 컴포넌트와 통신하기 위해서는 이벤트를 발생시켜 상위 컴포넌트로 신호를 보내면 된다. 

> 하위에서 상위로 데이터를 전달하는 방법은 뷰의 단방향 데이터 흐름에 어긋하는 구현 방방법이다. 다만 복잡한 애플리케이션을 구현해야 할 경우 이벤트 버스를 이용하여 데이터를 전달해야 하는 경우도 있다.

### 이벤트 발생과 수신형식

```javascript
// $emit()을 이용한 event 발생
this.$emit('이벤트명')
```

```html
<!-- v-on:속성을 이용한 event 수신 -->
<child-component v-on:이벤트명="상위 컴포넌트의 메서드명"></child-component>
```

**[⬆ back to top](#table-of-contents)**

## Vue라우터

### 라우팅(Routing)은 라우터(Router)를 이해하기 위한 선행 개념이므로 중요

라우팅이란 웹 페이지 간의 이동 방법을 말하며, SPA(Single Page Application)에서 주로 사용된다. 라우팅을 사용하면 깜빡거림 없이 화면을 매끄럽게 전환할 수 있으며, 사용자 경험을 향상할 수 있다.

### 뷰 라우터 CDN

뷰 라우터는 뷰에서 라우팅 기능을 구현할 수 있도록 지원하는 공식 라이브러리이다. 

```html
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```

| 태그                        | 설명                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `<router-link to="URL 값">` | 페이지 이동 태그, 화면에서는 <a>로 표시되며, `to`에 지정한 URL로 이동함 |
| `<router-view>`             | 페이지 표시 태그, 변경되는 URL에 따라 해당 컴포넌트를 뿌려주는 영역 |

### $mount() API란?

`$mount()` API는 `el` 속성과 동일하게 인스턴스를 화면에 붙이는 역할을 하며, 인스턴스를 생성할 때 `el`을 넣지 않았더라도 생성하고 나서 `$mount()`를 이용하면 강제로 인스턴스를 화면에 붙일 수 있다. 참고로, 뷰 라우터의 공식 문서는 모두 인스턴스 안에 `el`을 지정하지 않고, 생성된 인스턴스를 `$mount()`를 이용해 붙이는 식으로 안내하고 있다.

### 중첩된 라우트(Nested Router)

중첩된 라우트(Nested Router)는 라우터로 페이지를 이동할 때 최소 2개 이상의 컴포넌트를 화면에 나타낼 수 있다. 중첩된 라우트(Nested Router)를 사용하면 URL에 따라서 컴포넌트의 하위 컴포넌트가 다르게 표시된다.

```
/user/foo/profile                     /user/foo/posts
+------------------+                  +-----------------+
| User             |                  | User            |
| +--------------+ |                  | +-------------+ |
| | Profile      | |  +------------>  | | Posts       | |
| |              | |                  | |             | |
| +--------------+ |                  | +-------------+ |
+------------------+                  +-----------------+
```

**중첩된 라우트 구성을 통해 URL에 따라 하위 컴포넌트가 바뀌더라도 위와 같은 관계를 표현할 수 있다.**

### 네임드 뷰(Named View)

특정 페이지로 이동했을 때 여러 개의 컴포넌트를 동시에 표시하는 라우팅 방식이다. URL에 맞추어 같은 레벨에서 여러 개의 컴포넌트를 한 번에 표시할 때 사용한다. 

### 네임드 뷰 예제

```html
<div id="app">
  <router-view name="header"></router-view>
  <router-view></router-view>
  <router-view name="footer"></router-view>
</div>
```

```javascript
var Body = {template: '<div>This is Body</div>'}
var Header = {template: '<div>This is Body</div>'}
var Footer = {template: '<div>This is Body</div>'}

var router = new VueRouter({
  routes: [
    path:'/',
    components: {
    	default: Body,
    	header: Header,
    	footer: Footer
    }
  ]
})

var app = new Vue({
  el:'#app',
  router: router
})
```

**[⬆ back to top](#table-of-contents)**

## Vue HTTP 통신

### 웹 앱의  HTTP 통신 방법

웹앱에서 서버에 데이터를 요청하는 HTTP 통신은 필수로 구현해야 하는 기능이며, 이를 통해 사용자와 상호 작용에 따라 데이터를 동적으로 화면에 표시할 수 있다.

뷰에서도 ajax를 지원하기 위한 라이브러리를 제공하며, 뷰 리소스와 엑시오스(axios)가 있다. 

### axios 

`axios`는 뷰 커뮤니티에서 가장 많이 사용되는 HTTP 통신 라이브러리이다. 엑시오스는 Promise기반의 API 형식이 다양하게 제공되어 별도의 로직을 구현할 필요 없이 주어진 API만으로도 간편하게 원하는 로직을 구현할 수 있다.

| API 유형                                | 처리 결과                                                    |
| --------------------------------------- | ------------------------------------------------------------ |
| `axios.get('URL 주소').then().catch()`  | 해당 URL 주소에 대해 HTTP GET 요청을 보낸다. 서버에서 보낸 데이터를 정상적으로 받아오면 then()안에 정의한 로직이 실행되고, 오류가 발생하면 catch()에 정의한 로직이 수행 |
| `axios.post('URL 주소').then().catch()` | 해당 URL 주소에 대해 HTTP POST 요청을 보내며, 기본적인 동작은 get()과 동일 |
| `axios({ 옵션 속성 })`                  | HTTP 요청에 대한 자세한 속성들을 직접 정의하여 보낼 수 있다 데이터 요청을 보낼 URL, HTTP 요청방식, 보내는 데이터 유형, 기타 등등 |

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script> <!-- axios CDN -->
```

```javascript
new Vue({
  el: '#app',
  methods: {
    getData() {
			axios.get('https://raw.githubusercontent.com/joshua1988/doit-vuejs/master/data/demo.json')
      .then(res => {
        console.log(res)
        console.log(res.data)        
      })
    
    }
  }
})
```

**[⬆ back to top](#table-of-contents)**

## Vue 템플릿

### 뷰 템플릿이란?

**뷰 템플릿**이란 HTML, CSS 등의 마크업 속성과 뷰 인스턴스에서 정의한 데이터 및 로직들을 연결하여 **사용자가 브라우저에서 볼 수 있는 형태의 HTML로 변환해주는 속성**이다. 



### 데이터 바인딩

#### {{ }} - 콧수염 괄호

`{{}}`는 뷰 인스턴스의 데이터를 HTML 태그에 연결하는 가장 기본적인 텍스트 삽입 방식이다.  뷰 인스턴의 데이터를 HTML에서 표현하기 위해 사용한다.

#### v-bind

`v-bind`는 `id`, `class`, `style` 등의 HTML 속성 값에 뷰 데이터의 값을 연결할 때 사용하는 데이터 연결 방식이며, `v-bind` 속성으로 지정할 HTML 속성이나 props 속성 앞에 접두사로 붙인다.

```javascript
new Vue({
  el:'#app',
  data: {
		idA: 10,
    classA: 'container',
    styleA: 'color: blue',
  }
})
```

뷰 코드가 전반적으로 `v-` 접두사를 붙이는 형태이므로 가급적 `v-bind` 속성을 이용하는 것이 HTML 문법과 구분도 되고, 다른 사람이 코드를 파악하기도 쉽다.

### 자바스크립트 표현식

뷰의 템플릿에서도 자바스크립트 표현식을 사용할 수 있지만 아래와 같은 사항에 대해서 주의해야 한다.

1. 자바스크립트 선언문과 분기문은 사용할 수 없음
2. 복잡한 연산은 인스턴스 안에서 처리, 화면과 로직을 분리해야 함

```html
<div id="#app">
  {{ true ? 100 : 0 }}
</div>
```

**[⬆ back to top](#table-of-contents)**

### 디렉티브

뷰 디렉티브란 HTML 태그 안에 `v-` 접두사를 가지는 모든 속성들을 말하며 예시는 아래와 같다.

```html
<a v-if="isTrue"></a>
```

| 디렉티브 이름 | 역할                                                         |
| ------------- | ------------------------------------------------------------ |
| `v-if`        | 지정한 뷰 데이터 값의 참, 거짓 여부에 따라 해당 HTML 태그를 화면에 표시하거나 표시하지 않음 |
| `v-for`       | 지정한 뷰 데이터의 개수만큼 해당 HTML 태그를 반복 출력       |
| `v-show`      | `v-if`와 유사하지만 데이터의 참, 거짓 여부에 따라 해당 HTML 태그를 화면에 표시하거나 표시하지 않음 |
| `v-bind`      | HTML태그의 기본 속성과 뷰 데이터 속성을 연결                 |
| `v-on`        | 화면 요소의 이벤트를 감지하여 처리할 때 사용                 |
| `v-model`     | 폼(`form`)에서 주로 사용되는 속성으로 폼에 입력한 값을 뷰 인스턴스의 데이터와 즉시 동기화할 수 있고, 화면에 입력된 값을 저장하여 서버에 보내거나 `watch`같은 고급 속성을 이용하여 추가 로직을 수행 |

#### 조건문

`v-if`를 통해 엘리먼트의 표시여부를 제어할 수 있다. 브라우저의 console에 `app.seen = false`를 입력하면 엘리먼트의 표시를 숨길 수 있다. 

```html
<div id="app">
  <p v-if="seen">You can see me!</p>
</div>
```

```javascript
var app = new Vue({
  el: '#app',
  data: {
    seen: true,
  }
})
```

#### 반복문

```html
<div id="app">
  <ul>
    <li v-for="todo in todos">{{ todo.text }}</li>
  </ul>
</div>
```

```javascript
var app = new Vue({
  el:'#app',
  data: {
    todos: [
      {text: "재미있는 Javascript!"},
      {text: "디자인을 만드는 CSS~"},
      {text: "구조를 만드는 HTML!"},
    ]
  }
})
```

#### 이벤트 처리(사용자 입력 핸들링)

사용자와 앱의 상호작용을 위해 `v-on`디렉티브를 사용하여 `Vue 인스턴스`에서 메소드를 호출하는 이벤트 리스너를 추가할 수 있다. 

이 방법은 DOM을 건드리지 않고, 앱의 상태만을 업데이트한다. **모든 DOM의 조작은 Vue에 의해 처리되며 작성한 코드는 기본 로직에만 초점을 맞춘다.** 

```html
<button v-on:click="clickBtn">클릭</button>
```

```javascript
methods: {
  clickBtn() {
    alert('clicked');
  }
}
```

#### 디렉티브로 메서드 호출시 인자값 넘기기

디렉티브로 메서드 호출시 인자값을 넘기는 행위는 옳지 않다.   

**화면과 로직을 분리해야 한다.**

```html
<button v-on:click="clickBtn(10)">클릭</button>
```

```javascript
methods: {
  clickBtn(num) {
    alert('clicked ' + num + ' times');
  }
}
```

#### 캐싱에 대한 이해를 위해서 methods VS computed

```html
<div id="app">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">메시지 뒤집기</button>
</div>
```

```javascript
var app = Vue({
	el:'#app',
	data: {
		message: "hello Vue.js!"
	},
	methods: {
    reverseMessage() {
      this.message = this.message.split('').reverse().join('');
    }
  }
})
```

#### 양방향 바인딩 

```html
<div>
	<input type="text" v-model="message">  
  {{ message }}
</div>
```

Vue는 입력과 앱의 상태를 양방향으로 바인딩하는 `v-model`디렉티브(directive)를 제공한다.

> Vue also provides the `v-model` directive that makes two-way binding between form input and app state a breeze:

### 고급 템플릿 기법 

#### computed 속성

HTML에 `{{ }}`를 사용해 데이터를 바인딩할 수도 있지만 `computed 속성`을 사용하면 아래와 같은 이점을 얻을 수 있다.

1. data 속성 값의 변화에 따라 자동으로 연산
2. **캐싱**, 즉 동일한 연산을 반복하지 않기 위해 연산의 결과값을 미리 저장해놓고, 필요할 때 불러오는 동작

```javascript
new Vue({
  el:'#app',
  data: {
    message: 'Hello Vue.js!'
  },
  computed: {
  	reversedMessage() { // reversedMessage가 미리 연산결과를 가지고 있음
      return this.message.split('').reverse().join('') // 결과만 표시
    }  
  }
})
```

**[⬆ back to top](#table-of-contents)**



## 뷰 컴포넌트 구성방법

### HTML 파일에서 Vue 코드를 작성하는 방식의 한계점 

HTML 파일에 여러 개의 컴포넌트를 등록하는 방식은 구문 강조가 되어 있지 않아 마크업이 어떻게 표현될지 예상하기 어렵다.

- 에디터나 IDE의 도움을 받을 수 없으므로 오탈자를 찾기 어려움
- 들여쓰기가 어려워 태그의 구조 및 관계를 파악하기 어려움

```javascript
// 컴포넌트 1
Vue.component('header', {
  template: `...`
})
// 컴포넌트 2
Vue.component('contents', { template: `...` })
// 컴포넌트 3
Vue.component('footer', { template: `...` })
```

### 싱글 파일 컴포넌트

싱글 파일 컴포넌트는 여러 개의 컴포넌트 및 template 속성을 추가할 경우 발생할 수 있는 가독성 문제를 해소해준다. 싱글 파일 컴포넌트는 `.vue`확장자 파일을 통해 프로젝트 구조를 구성하며 1개의 컴포넌트와 동일하다.

```html
<template>
	<!-- HTML -->
  <!-- 화면에 표시할 요소들을 정의하는 영역 -->
  <!-- HTML + Vue 데이터 바인딩 -->
</template>

<script>
export default {
  // Javascript
  // 뷰 컴포넌트의 내용을 정의하는 영역
  // template, data, methods
}	
</script>

<style>
	/* CSS */
  /* 템플릿에 추가된 HTML 태그의 스타일 속성 정의 */
</style>
```

#### 싱글 파일 컴포넌트 예제

```vue
<template>
<div>
	<button>{{ message }}</button>  
</div>
</template>

<script>
export default {
  data: {
    message: "click this button"
  }
}
</script>

<style>
  span {
    font-size: 1.2em;
  }
</style>
```

### Vetur 설치

VSCode의 Extensions에서 설치 가능

- Visual Studio Code에서 Vue 문법을 체크하는 툴
- Vue 문법에 따라 색상이 변하고, 기본 템플릿 코드도 만들어져 매우 편리

**[⬆ back to top](#table-of-contents)**

## Vue CLI

**Vue CLI 명령어를 통해 애플리케이션을 개발하기 위한 초기 구조를 쉽게 구성 가능하다**

- Vue CLI 명령어를 사용하여 생성한 프로젝트 템플릿을 통해 웹팩 같은 모듈 번들러를 프로젝트 자체에 포함하여 바로 사용할 수 있다.
- 템플릿은 `.vue`파일을 HTML, CSS JavaScript 파일로 변환해주는 Vue Loader를 포함하고 있다.

### 웹팩

싱글 파일 컴포넌트 체계를 사용하기 위해서는  `.vue`파일을 웹 브라우저가 인식할 수 있는 형태의 파일로 변환해야 한다. 이를 돕는 대표적인 도구가 웹팩(`Webpack`)이다. 웹팩(`Webpack`)은 웹 앱의 자원(HTML, CSS, 이미지)들을 자바스크립트 모듈로 변환해 하나로 묶어 웹의 성능을 향상시켜 주는 자바스크립트 모듈 번들러이다.

## Vue CLI를 활용한 프로젝트 생성법

### 뷰 CLI 설치

```bash
$ npm install vue-cli -global
```

### 뷰 CLI로 프로젝트 생성하기 

```bash
$ vue init webpack-simple
```

### 프로젝트 생성 후 Vue 앱을 구동하기 위한 라이브러리 다운로드

```bash
$ npm install
```

### Vue 앱 실행

>  생성 후에는 실행을 꼭 테스트해야 한다.

```bash
$ npm run dev
```

**[⬆ back to top](#table-of-contents)**

















## Reference Docs

- [Vue.js Tutorial](https://kr.vuejs.org/v2/guide/index.html)
- [OOD - 커플링이란 무엇이며, 어떻게 줄일 수 있을까?](https://vandbt.tistory.com/13)





















