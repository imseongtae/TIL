# Javascript


## Table of Contents

1. [Types](#types)
1. [DOM 탐색](#DOM-탐색)
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


## Destructuring

## spread

## class

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



메모리 관리 하이서울

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


