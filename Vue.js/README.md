# Vue.js

Vue.js는 가볍고 단순한 구조를 가지고 있어서 기존의 프로젝트에도 쉽게 적용할 수 있다. 또한 재사용이 가능한 컴포넌트 기반이므로 이를 이용하거나 ES6를 이용할 수도 있다. 그리고 routing, vuex를 사용해 한 곳에서 애플리케이션 전체에서 사용하는 데이터를 효과적으로 관리할 수도 있다. 

양방향 데이터 바인딩을 이용해 UI와 데이터 모델간의 reactivity 기능을 만들 수 있다는 장점이 있다.



## Table of Contents

1. [뷰 인스턴스](#뷰-인스턴스)
1. [컴포넌트를 사용한 작성방법](#컴포넌트를-사용한-작성방법)
1. [선언적 렌더링](#선언적-렌더링)
1. [라이프 싸이클](#라이프-싸이클)
1. [조건문과 반복문](#조건문과-반복문)
1. [사용자 입력 핸들링](#사용자-입력-핸들링)
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







## 조건문과 반복문

### 조건문

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

### 반복문

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

**[⬆ back to top](#table-of-contents)**

## 사용자 입력 핸들링

사용자와 앱의 상호작용을 위해 `v-on`디렉티브를 사용하여 `Vue 인스턴스`에서 메소드를 호출하는 이벤트 리스너를 추가할 수 있다. 

이 방법은 DOM을 건드리지 않고, 앱의 상태만을 업데이트한다. **모든 DOM의 조작은 Vue에 의해 처리되며 작성한 코드는 기본 로직에만 초점을 맞춘다.** 

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



Vue는 입력과 앱의 상태를 양방향으로 바인딩하는 `v-model`디렉티브(directive)를 제공한다.

> Vue also provides the `v-model` directive that makes two-way binding between form input and app state a breeze:

**[⬆ back to top](#table-of-contents)**















## Reference Docs

- [Vue.js Tutorial](https://kr.vuejs.org/v2/guide/index.html)
- [OOD - 커플링이란 무엇이며, 어떻게 줄일 수 있을까?](https://vandbt.tistory.com/13)





















