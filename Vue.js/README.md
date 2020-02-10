# Vue.js



양방향 바인딩, 속도가 빠름

Vue.js는 가볍고 단순한 구조를 가지고 있다.그래서 기존의 프로젝트에도 쉽게 적용할 수 있다. 또한 재사용이 가능한 컴포넌트 기반이므로 이를 이용하거나 ES6를 이용할 수도 있다. 그리고 routing, vuex를 사용해 한 곳에서 애플리케이션 전체에서 사용하는 데이터를 효과적으로 관리할 수도 있다. 

양방향 데이터 바인딩을 이용해 UI와 데이터 모델간의 reactivity 기능을 만들 수 있다.



## Table of Contents

1. [Primitive Types](#Primitive-Types)
1. 
1. Reference Docs

---

## Vue.js 시작을 위한 script

```html
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```



## 선언적 렌더링([Declarative Rendering](https://vuejs.org/v2/guide/#Declarative-Rendering))

Vue.js는 간단한 템플릿 구문을 사용해 DOM에서 데이터를 선언적으로 렌더링할 수 있는 시스템이 있다.

```html
<div id="app">
  {{ message }}
</div>
```

```javascript
var app = new Vue({
	el: '#app',
	data: {
		message: '반가워 Vue!'
	}
})
```



## 조건문과 반복문([Conditionals and Loops](https://vuejs.org/v2/guide/#Conditionals-and-Loops))

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

## 사용자 입력 핸들링([사용자 입력 핸들링](https://kr.vuejs.org/v2/guide/index.html#사용자-입력-핸들링))

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
  }, //end data
  methods: {
    reverseMessage: function() {
			this.message = this.message.split('').reverse().join('');
    }
  }
})
```

Vue는 입력과 앱의 상태를 양방향으로 바인딩하는 `v-model`디렉티브(directive)를 제공한다.

> Vue also provides the `v-model` directive that makes two-way binding between form input and app state a breeze:

## 컴포넌트를 사용한 작성방법

컴포넌트 시스템은 Vue의 또 다른 중요한 개념인데, 이는 작고 독립적이며, 재사용할 수 있는 컴포넌트로 구성된 대규모 애플리케이션을 구축할 수 있게 해주는 추상적 개념이다. 

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













## Reference Docs

- [Vue.js Tutorial](https://kr.vuejs.org/v2/guide/index.html)





















