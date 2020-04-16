# Node.js

## Node.js란 무엇인가?

**Node.js** 는 **서버사이드 자바스크립트**이며 구글의 자바스크립트 엔진인 **V8**을 기반으로 구성된 **자바스크립트 런타임**이다. Node.js는 이벤트 기반, 논블로킹 I/O 모델을 사용해 가볍고 효율적이다.

### 서버로서의 Node.js

서버는 네트워크를 통해 클라이언트에 정보나 서비스를 제공하는 컴퓨터 또는 프로그램을 말한다. 서버는 클라이언트의 요청에 대해 응답을 하는데, 응답으로 항상 Yes를 하는 것은 아니고, No를 할 수도 있다. 



- 자바스크립트 기반
- 이벤트 기반의 프로그래밍 모델
- NPM을 통한 다양한 확장 모듈들



## Table of Contents

1. [Hello World!](#Hello-World)
1. [File System](#File-System)
1. [Event Module](#Event-Module)
1. [Inherit](#Inherit)

---



## Hello World!

Node.js를 이용하면 단 몇 줄만으로 간단하게 웹 서버를 만들 수 있다.

```javascript
var server = require('http'); // http 모듈을 가지고 옴

server.createServer(function(req, res){
  res.writeHead(200, { 'Content-Type' : 'text/plain' });
  res.end("Hello node.js! \n");
}).listen(3000, 'localhost');

console.log('Server is running at http://localhost:3000/');
```



## File System

- fs.readFile(filename, [options], callback) : filename의 파일을 [options]의 방식으로 읽은 후 callback으로 전달된 함수를 호출합니다. (비동기적) 
- fs.readFileSync(filename, [options]) : filename의 파일을 [options]의 방식으로 읽은 후 문자열을 반환합니다.(동기적)
- fs.writeFile(filename, data, [options], callback) : filename의 파일에 [options]의 방식으로 data 내용을 쓴 후 callback 함수를 호출합니다.(비동기적) 
- fs.writeFileSync(filename, data, [options]) : filename의 파일에 [options]의 방식으로 data 내용을 씁니다.(동기적)

```javascript
var fs = require('fs');

fs.readFile('text.txt', 'utf8', function(err, data) {
  console.log('비동기적 읽기 \n' + data);
  console.log('\n비동기적 읽기 끝')
});

var text = fs.readFileSync('text.txt', 'utf8');
console.log('동기적 읽기 시작 \n' + text + '\n동기적 읽기 끝 \n')
```



## Event Module

노드의 많은 객체는 이벤트를 발생시키는데, 이러한 객체들은 바로 `events.EventEmitte` 라는 인스턴스를 이용한다.

- emitter.addListener(event, listener) : on() 메소드와 같습니다. 이벤트를 생성하는 메소드입니다.
- emitter.on(event, listener) : addListener()과 동일합니다. 이벤트를 생성하는 메소드입니다.
- emitter.once(event, listener) : 이벤트를 한 번만 연결한 후 제거합니다.
- emitter.removeListener(event, listener) : 특정 이벤트의 특정 이벤트 핸들러를 제거합니다. 이 메소드를 이용해 리스너를 삭제하면 리스너 배열의 인덱스가 갱신되니 주의해야 합니다.
- emitter.removeAllListeners([event]) : 모든 이벤트 핸들러를 제거합니다.
- emitter.setMaxListeners(n) : n으로 한 이벤트에 최대허용 개수를 정해줍니다. node.js는 기본값으로 한 이벤트에 10개의 이벤트 핸들러를 작성할 수 있는데, 11개 이상을 사용하고 싶다면 n값을 넘겨주면 됩니다. n값으로 0을 넘겨 주면 연결 개수 제한이 사라집니다.
- emitter.emit(eventName[, ...args]) : 이벤트를 발생시킵니다.



### 이벤트 생성(이벤트 핸들러 연결)

- on
- addListener

```javascript
var EventEmitter = require('events');
var custom_event = new EventEmitter();

//event 이름: ham, 
custom_event.on('ham', function() { 
  console.log('이벤트 콜') // event listener
})
custom_event.emit('ham');
```



### 이벤트 제거

```javascript
var EventEmitter = require('events');
var custom_event = new EventEmitter();

custom_event.on('ham', function() {
  console.log('이벤트 콜')
})

custom_event.removeAllListeners(); // 모든 이벤트 리스너를 제거
custom_event.emit('ham');
```



## Inherit

### 자바스크립트에서 상속

```javascript
function Foo() {

}
Foo.prototype = {
  bar :function() {
    console.log('Foo_bar 실행')
  }
}

function Bar() {

}
Bar.prototype = Object.create(Foo.prototype);
Bar.prototype.baz = function() {
  console.log('Bar_baz 실행')
}

Foo.prototype.bar();
Bar.prototype.bar();
Bar.prototype.baz();
```



### util.inherits() 메소드를 이용한 상속

```javascript
function Foo() {}
Foo.prototype = {
  bar :function() {
    console.log('Foo_bar 실행')
  }
}

function Bar() {}
// Object.create() 메서드는 지정된 프로토타입 객체 및 속성(property)을 갖는 새 객체를 만듦
Bar.prototype = Object.create(Foo.prototype); 
Bar.prototype = Foo.prototype;

Bar.prototype.baz = function() {
  console.log('Bar_baz 실행')
}

Foo.prototype.bar();
Bar.prototype.bar();
Bar.prototype.baz();
```



