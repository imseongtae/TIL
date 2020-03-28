# Node.js

**Node.js** 는 **서버사이드 자바스크립트**이며 구글의 자바스크립트 엔진인 **V8**을 기반으로 구성된 일종의 소프트웨어 시스템이다. 

- 자바스크립트 기반
- 이벤트 기반의 프로그래밍 모델
- NPM을 통한 다양한 확장 모듈들



## Table of Contents

1. [File System](#File-System)
1. 

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

