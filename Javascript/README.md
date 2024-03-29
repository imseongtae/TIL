# Javascript

![js](https://user-images.githubusercontent.com/40027211/72528195-d1e27b80-38ad-11ea-9d5f-cdd9ef25aaa8.png)







## Table of Contents

1. [Types](#types)
1. [DOM 탐색](#DOM-탐색)
1. [생성자](#생성자)
1. [class](#class)

1. [Destructuring](#destructuring)

1. [Javascript for Web](#Javascript-for-Web)


1. [To Do List](./ToDoList.md)

---



## 배열 내장 함수

| 속성 | 설명 |
|---|---|
| `push` | 배열의 마지막 인덱스에 요소를 추가하고 배열의 길이를 반환 |
| `pop` | 배열의 마지막 요소를 잘라내 반환 |
| `shift` | 배열의 첫 번째 요소를 제거한 후 배열의 자리를 왼쪽으로 이동 |
| `unshift` | 배열의 첫 번째 위치에 요소를 추가한 후 배열의 자리를 오른쪽으로 이동 |
| `splice` | 배열 요소를 갈아 끼울 때 사용, 요소를 끼워넣을 수도 있고, 삭제만 할 수도 있음 |
| `sort` | 배열 안의 요소를 정렬합니다. 인수로는 실제 비교를 담당하는 함수와 참조를 넘김 |


## 생성자
Javascript airbnb 스타일 가이드를 따른다.

**[⬆ back to top](#table-of-contents)**

## Object-shorthand
Object-shorthand(객체 약식구문)을 통해  
복잡한 객체 리터럴(표현 방법)을 깔끔하게 정의할 수 있다.  
`key`이름으로 선언된 값이 존재한다면, 바로 매칭시켜주는 문법이다.

```javascript
const foo_properties = {
  x: x, 
  y: y, 
  z: z,
};

const foo_method = {
  a: function() {},
  b: function() {}
};
```

```javascript
const foo_properties = {x,y,z};

const foo_method = {
  a() {},
  b() {}
};
```

[링크 - airbnb style guide Object-shorthand 내용](https://github.com/airbnb/javascript#es6-object-concise)

```javascript
const lukeSkywalker = 'Luke Skywalker';

// bad
const obj = {
  lukeSkywalker: lukeSkywalker,
};

// good
const obj = {
  lukeSkywalker,
};
```

## class
클래스를 만들어놓고 클래스를 통해 객체를 생성하면 같은 형태를 지닌  
객체를 만들 때 객체들이 지닌 값과 함수를 보기 좋은 형태로 관리할 수 있다.

```javascript
class Burger {
  constructor(name) {
    this.name = name;
    this.ingredients = [];
  }
  addIngredient(ingredient) {
    this.ingredients.push(ingredient)
  }
  print(){
    console.log('주문한 '+this.name+'는 다음 재료를 가지고 있습니다.')
    console.log(this.ingredients.join(','))
  }
}

const burger = new Burger('아보카도 버거')
burger.addIngredient('아보카도');
burger.addIngredient('양파');
burger.addIngredient('양상추');

burger.print();
```


## Destructuring
배열, 객체, 반복 가능한 객체에서 값을 추출하여 변수 혹은 상수에 할당하는 문장을 말하며, ES6부터 도입되었다.


### 객체 비구조화 할당
비구조화 할당 문법을 통해서 객체 안에 있는 값을 추출해 변수 혹은 상수로 선언할 수 있다.

```javascript
const object = {a:1, b:2};
const {a, b} = object;

console.log(a) // 1
console.log(b) // 2
```

기본값도 지정가능함!

```javascript
const object = {a:1};
const {a, b = 7} = object;

console.log(a) // 1
console.log(b) // 7
```



### 배열 비구조화 할당
배열 안에 있는 원소를 새로 선언해주고 싶을 때 사용하면 유용하다.
객체 비구조화 할당처럼 기본값도 지정가능하며 함수의 인자로 넘길 수 있다.

```javascript
const arr = [1,2];
const [a, b] = arr;

function print([a,b]) {
  console.log(a, b) // 1 2
}

print(arr);
```


## spread


## class

```javascript



```

## callback

```javascript
function increase(number, callback) {
  setTimeout(() => {
    const result = number + 10;
    if (callback) {
      callback(result);
    }
  }, 1000);
}

increase(0, result => {
  console.log(result);
});
```



**[⬆ back to top](#table-of-contents)**


## Javascript for Web

### classList

| 속성 | 설명 |
|---|---|
| `add` | 지정한 클래스 값을 추가, 만약 추가하려는 클래스가 존재한다면 무시 |
| `remove` | 지정한 클래스 값을 제거 |
| `item` | 콜렉션의 인덱스를 이용하여 클래스값을 반환 |
| `toggle` | 클래스가 존재하면 제거, 존재하지 않으면 추가 |
| `contains` | 지정한 클래스 값이 Element의 속성에 존재하는지 학인함 |
| `replace` | 존재하는 클래스를 새로운 클래스로 교체 |


```javascript
addBtn.classList.add('active');
addBtn.classList.contains('active');
addBtn.classList.replace('oldActive', 'newActive');
```

**[⬆ back to top](#table-of-contents)**


### 이벤트 위임



**[버블링과 캡처링에 대해 이해를 얻은 캡틴 판교님의 글](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)**

#### 이벤트 버블링(Event Bubbling)
이벤트 버블링은 특정 요소에서 이벤트가 발생했을 때 
해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성을 의미한다

```html
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>
```

```javascript
var divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent);
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```

#### 이벤트 캡쳐(Event Capture)
이벤트 캡쳐는 이벤트 버블링과 반대 방향으로 진행되는 이벤트 전파 방식입니다




**[⬆ back to top](#table-of-contents)**

### DOM 탐색

노드는 HTML 문서내 구조를 이루고 있는 요소를 말한다.  
HTML 문서의 요소는 부모, 자식, 형제 구조를 이루므로 **특정 요소를 기준** 삼아서 서로 상대적으로 참조할 수 있다. 

| 속성 | 설명 |
|---|---|
| `parentNode` | 부모 노드를 선택합니다. |
| `children` | 자식 노드를 선택합니다. |
| `previousSibling` | 이전 형제를 선택합니다. |
| `nextSibling` | 다음 형제를 선택합니다.  |


**[⬆ back to top](#table-of-contents)**


### Node 생성/삽입/삭제

| 속성 | 설명 |
|---|---|
| `createElement(요소 이름)` | 새로운 요소 노드 객체를 생성 |
| `appendChild(삽입할 노드)` | 인자로 넘긴 노드를 마지막 자식 노드로 삽입 |
| `removeChild(자식 노드)` | 노드에서 인자로 넘긴 자식 노드를 삭제 |
| `replaceChild(새로운 노드, 자식노드)` | 인자로 받은 자식 노드를 제거하고, 새로운 노드로 바꿈  |


**[⬆ back to top](#table-of-contents)**


### Storage 메서드

| 속성 | 설명 |
|---|---|
| Storage.setItem() | 인자로 key, value를 전달해 Storage에 저장 |
| Storage.getItem() | 인자로 key를 전달하여 Storage에 저장된 값을 조회 |
| Storage.removeItem() | 인자로 key을 전달하면 해당 키가 Storage에서 지워짐 |
| Storage.clear() | Storage 전체를 비움 |


### localStorage에 데이터 넣어보기
`localStorage`에 데이터를 저장할 때 key/value 형식으로 저장할 수도 있지만, 객체 형태로 저장하려면 `JSON.stringify()`를 통해 객체 타입을 문자열 타입으로 변환하여 저장해야 한다. 또한 반대로 `localStorage`의 데이터를 가져올 때는 `JSON.parse()`를 통해 문자열을 객체 타입으로 변환하여 가져와야 합니다. 

```javascript
const TODOS_LS = "toDos";
const toDos = [];

for (let i = 0; i < 5; i++) {
  const toDoObj = {
    text:"안녕하세요",
    id: i + 1
  }
  toDos.push(toDoObj);  
}

localStorage.setItem(TODOS_LS, JSON.stringify(toDos))
```


### localStorage 활용

#### JSON.stringify
`localStorage.setItem(TODOS_LS, toDos)`처럼 `setItem()`메소드의 인자에 자바스크립트 데이터를 직접 넣으면 `LocalStorage`에는 `[object Object]`처럼 데이터가 들어간다.

왜냐하면 `LocalStorage`에는 자바스크립트의 data를 저장할 수 없기 때문이다. `LocalStorage`는 모든 데이터를 `string`으로 저장한다. 그래서 자바스크립트 `object`가 `string`이 되도록 바꾸고 저장해야 한다. 이를 위해서 `JSON.stringify()`메소드를 사용해야 하는데, `JSON.stringify()`는 인자로 전달된 자바스크립트 `object`를 `string`으로 바꿔준다.

```javascript
function saveToDos(){
  localStorage.setItem(TODOS_LS, JSON.stringify(toDos));
}
```

#### JSON.parse
`localStorage.getItem()`으로 데이터를 불러온 경우 불러온 데이터가 `string`이라는 문제가 생긴다! 이를 자바스크립트에서 활용하기 위해서는 `JSON(Javascript Object Notation)`을 사용해야 한다! JSON을 통해 string을 object로, object를 string으로 변경할 수 있다.

`JSON.parse()`를 사용하면 데이터를 가져올 때 자바스크립트가 다룰 수 있도록 `string`을 `object`로 바꿔준다!

아래는 `localStorage`에서 가져온 코드를 `JSON.parse()`메서드를 통해 `string`을 `object`로 바꾸었다.

```javascript
function loadToDos() {
  const loadedToDos = localStorage.getItem(TODOS_LS);
  if(loadedToDos !== null) {
    const parsedToDos = JSON.parse(loadedToDos);

    parsedToDos.forEach(toDo => {
      paintToDo(toDo.text);
    });
  } 
}
```
