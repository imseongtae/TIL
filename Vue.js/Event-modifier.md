# Event 수식어

이벤트가 발생하면 크롬이나 파이어폭스 같은 브라우저는 bubble, capture, target 이라는 3가지 방법을 이용해 어디에서 이벤트가 발생했는지 찾는다.

## Bubble

bubble은 이벤트가 발생한 대상 엘리먼트에서 부모, 조상 엘리먼트 형태로 진행되며, 이를 이벤트 버블링이라고 한다. 

### 예시

```html
<div id="app">
  <div class="container">
    <div id="outer" class="blue white-text" @click="handleClickEvent">
      Outer
      <div id="middle" class="yellow" @click="handleClickEvent">
        Middle
        <div id="inner" class="cyan" @click="handleClickEvent">
          Inner
        	<button id="button" @click="handleClickEvent">클릭</button>
        </div>
      </div>
    </div>
  </div>
</div>
```

```javascript
methods: {
	handleClickEvent() {
    console.log(`handleClickEvent target: ${$event.target.id}`+ ` currentTarget: ${$event.currentTarget.id}`)
  }
}
```

 ![bubble button](https://user-images.githubusercontent.com/40027211/74607245-8f18fb00-511a-11ea-812d-f472142f241c.PNG)

### 각각의 영역을 클릭할 경우 콘솔창 확인

![complexBubbling](https://user-images.githubusercontent.com/40027211/74607605-97266a00-511d-11ea-8864-cd56ba0541f8.PNG)



### DOM 요소 비교를 통해서 로직을 실행하는 방법

```javascript
methods: {
  handleClickEvent(event) {
    if (event.target.nodeName.toLowerCase() === 'button') {
      // 해당 요소일 경우 특정 로직을 수행
      console.log('버튼입니다.')
    } else {
      console.log(`handleClickEvent target: ${$event.target.id}`+ ` currentTarget: ${$event.currentTarget.id}`)
    }
  }
}
```



![bubble button](https://user-images.githubusercontent.com/40027211/74607245-8f18fb00-511a-11ea-812d-f472142f241c.PNG)

### v-on 디렉티브 수식어

| 설명              | 기능                                                         |
| ----------------- | ------------------------------------------------------------ |
| stopPropagation() | 이벤트 버블링을 중지                                         |
| stop              | 이벤트 버블링을 중지                                         |
| prevent           | 브라우저가 이벤트 발생 시 기본적으로 발생하는 동작을 중지. 대표적으로 submit이나 앵커 태그의 클릭 이후 발생할 이벤트를 중지하는데 사용 |
| capture           | 이벤트 버블링과 반대되는 동작을 수행                         |
| self              | 이벤트가 전파되지 않고 자신에서만 이벤트가 발생              |
| once              | 이벤트가 한 번만 발생                                        |
| passive           | 휴대폰 같은 터치 이벤트 기반의 수동적인 이벤트 리스닝 성능 향상에 활용 |



### stopPropagation 예시

![bubble button](https://user-images.githubusercontent.com/40027211/74607245-8f18fb00-511a-11ea-812d-f472142f241c.PNG)

```javascript
methods: {
	handleClickEvent() {
    $event.stopPropagation();
    console.log(`handleClickEvent target: ${$event.target.id}`+ ` currentTarget: ${$event.currentTarget.id}`)
  }
}
```

![stopPropagation](https://user-images.githubusercontent.com/40027211/74607565-3ac34a80-511d-11ea-98f6-35e19d12de3b.PNG)






