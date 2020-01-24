# To Do List

HTML, CSS, Javascript 를 활용해서 만들어본 
To Do List 입니다. vanillaJS의 실력향상을 위해서 
ES5의 문법을 사용했습니다. 

단, 호이스팅을 피하기 위해서 변수선언 키워드는 ES6의 `let`,`const`를 사용했습니다.


## Table of Contents

1. [HTML](#HTML)
1. [CSS](#CSS)
1. [Javascript](#Javascript)




---


## HTML 

`body`태그 내부의 HTML 태그만 정리했습니다.

```html
<div class="todo-container">
  <h1 id="title">할 일 목록</h1>
      
  <form id="todo-form">
    <input type="text" id="userInput">
    <input type="submit" value="목록 추가" id="add-btn">
  </form>

  <ul id="list">
    <li>To Do List</li>
  </ul>
</div>
```

## CSS

CSS를 통해 간단한 디자인을 입힘


```css
.todo-container {
  margin: 30px auto;
  width: 600px;
  border: 1px solid #ddd;
}
input {
  padding: 8px 14px;
}
#add-btn {
  border: 0;
  border-radius: 5px;
  background-color: #B5E2DF;
  font: bold 14px/1.2 sans-serif;
}
ul {
  padding: 0;
  list-style-position: inside;
}
li {
  padding: 10px 0 10px 15px;
  border-bottom: 1px solid #999;
  cursor: pointer;
}
.active {background-color: #abc;}
```


## Javascript version.1

목록추가 기능을 구현한 Javascript 코드입니다.
Javascript는 처음 로딩된 문서를 기억할 뿐 동적으로 추가된, 즉 사용자 입력에 의해 추가된 내용은 다시 확인하지 않으므로 `li`요소 각각에 이벤트를 걸어주는 것이 아니라 `ul`목록 태그에 이벤트를 걸어준다.  

`event.target`을 통해 클릭한 객체의 속성값을 통해 동적으로 `li`배열의 길이를 알아낼 수 있고,  
아래와 같이 작성한다.
`event.target.parentNode.children` 


```javascript
const title = document.getElementById('title');
const list = document.getElementById('list');

const todoForm = document.getElementById('todo-form');
const userInput = document.getElementById('userInput');
const addBtn = document.getElementById('add-btn');

function activeItem(event) {
  if(event.target.nodeName === "LI") {
    title.innerHTML = event.target.innerText;

    for (let i = 0; i < event.target.parentNode.children.length; i++) {
      event.target.parentNode.children[i].removeAttribute('class');
    }
    event.target.setAttribute('class', 'active');
  } 
}

list.addEventListener('click', activeItem)
todoForm.addEventListener('submit', function(e){
  e.preventDefault();
  // let text = userInput.value;
  list.innerHTML += '<li>' + userInput.value + '</li>';
  userInput.value = '';
  console.log('실행 흐름이 이어지냐?');
})
```

