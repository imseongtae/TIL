# Node.js를 위한 Javascript



## Table of Contents

1. [객체 리터럴](#객체-리터럴)
1. [화살표 함수](#화살표-함수)
1. [Promise](#Promise)
1. [async/await](#async/await)

---



## 객체 리터럴

- 콜론과 `function` 을 더 이상 사용하지 않아도 되므로 코드량을 줄일 수 있다.

```javascript
var sayNode = function() {
  console.log('Node');
};
var es ='ES';
const newObject = {
  sayJS() {
    console.log('JS');
  },
  sayNode,
  [es + 6]:'Fantastic',
};

newObject.sayNode(); // Node
newObject.sayJS(); // JS
console.log(newObject.ES6); // Fantastic
```





## 화살표 함수

### this 바인딩 차이

```javascript
var relationship1 = {
  name:'zero',
  friends: ['nero','hero','xero'],
  logFriends: function() {
    var that = this; // relationship1을 가리키는 this를 that에 저장
    // 상위 스코프의 this를 사용하기 위해 변수에 할당
    this.friends.forEach(function(friend) {
      console.log(that.name, friend);
    });
  },
};
relationship1.logFriends();

const relationship2 = {
  name:'zero',
  friends: ['nero','hero','xero'],
  logFriends() {
    this.friends.forEach(friend => { // 상위 스코프의 this를 그대로 물려받음
      console.log(this.name, friend);
    });
  },
};
relationship2.logFriends();
```



## Promise

- new Promise를 통해 프로미스 객체를 생성
- 생성자의 인자에 `resolve`, `reject`를 매개변수로 갖는 콜백함수를 넣어줌
- `promise`변수에 `then`과 `catch` 메서드를 붙일 수 있음
- `resolve`, `reject`에 넣어준 인자는 각각 `then`과 `catch` 메서드에서 받을 수 있음
- 

```javascript
const condition = false;
const promise = new Promise((resolve, reject) => {
  if (condition) {
    resolve('success')
  } else {
    reject('error')
  }
})

promise
  .then((message) => {
    console.log(message); // 성공(resolve)한 경우
  })
  .catch((err) => {
    console.error(err) // 실패(reject)한 경우
  })

```



### then이나 catch에  다른 then이나 catch를 붙이는 방법

```javascript
const condition = true;
const promise = new Promise((resolve, reject) => {
  if (condition) {
    resolve('success')
  } else {
    reject('error')
  }
})

promise
  .then((msg) => {
    return new Promise((resolve, reject) => {
      resolve(msg)
    })
  })
  .then((msg2) => {
    console.log(msg2)
    return new Promise((resolve, reject) => {
      resolve(msg2)
    })
  })
  .then((msg3) => {
    console.log(msg3)
  })
  .catch(error => {
    console.error(error)
  })

```



### 콜백을 프로미스로 바꾸는 예시

```javascript
function findAndSaveUser(Users) {
  Users.findOne({}, (err, user) => { // 첫 번째 콜백
    if (err) {
      return console.error(err);
    }
    user.name = 'zero';
    user.save((err) => { // 두 번째 콜백
      if (err) {
        return console.error(err);
      }
      Users.findOne({gender: 'm'}, (err, user) => { // 세 번째 콜백
        // 생략
      });
    });    
  });
}
```



- 코드의 깊이가 깊어지지 않음
- `then`메서드들은 순차적으로 실행
- 에러도 `catch`에서 한 꺼번에 처리
- 메서드가 **프로미스 방식**을 지원해야 아래처럼 바꿀 수 있음

```javascript
function findAndSaveUser(Users) {
  Users.findOne({})
    .then(user => {
      user.name = 'zero';
      return user.save();
    })
    .then(user => {
      return Users.findOne({gender: 'm'});
    })
    .then((user) => {

    })
    .catch(err => {
      console.error(err);
    })
}
```





## async/await

노드 7.6 버전부터 지원되는 기능이며, 자바스크립트 스펙은 ES2017이다. async/await 문법은 프로미스를 사용한 코드를 한 번 더 깔끔하게 줄여준다.

```javascript
function findAndSaveUser(Users) {
  Users.findOne({})
    .then((user) => {
      user.name ='zero';
      return user.save();
    })
    .then((user) => {
      return Users.findOne({ gender:'m' });
    })
    .then((user) => {
      // 생략
    })
    .catch(err => {
      console.error(err);
    });
}
```

### async/await 문법

```javascript
async function findAndSaveUser(Users) {
  try {
    let user = await Users.findOne({});
    user.name ='zero';
    user = await user.save();
    user = await Users.findOne({ gender:'m' });
    // 생략 
  } catch (error) {
    console.error(error);
  }
}
```



## Front-end와 협업을 위한 JS

### AJAX

**AJAX**(Asynchronous Javascript And XML)는 비동기적 웹 서비스를 개발하기 위한 기법이다. 이름에 XML이 들어가 있지만 꼭 XML을 사용해야 하는 것은 아니며, 요즘에는 JSON을 많이 사용한다. **AJAX**는 페이지 이동 없이 서버에 요청을 보내고 응답을 받는 기술이다. 

- jQuery나 axios 같은 라이브러리 없이 자바스크립트가 기본으로 제공하는 방식의 요청

```javascript
var xhr = new XMLHttpRequest();
  xhr.onreadystatechange = function() { // 요청에 대한 콜백
    if (xhr.readyState === xhr.DONE) { // 요청이 완료되면
      if (xhr.status === 200 || xhr.status === 201) { // 응답 코드가 200이나 201이면
        console.log(xhr.responseText); // 서버에서 보내주는 값
      } else {
        console.error(xhr.responseText);
      }
    }
  };
  xhr.open('GET','https://www.zerocho.com/api/get'); // 메서드와 주소 설정
  xhr.send(); // 요청 전송
```

- onreadystatechange 대신 `onload`와 `onerror`로 성공과 실패를 구별할 수도 있음

```javascript
var xhr = new XMLHttpRequest();
xhr.onload = function() {
  if (xhr.status === 200 || xhr.status === 201) {
    console.log(xhr.responseText);
  }
};
xhr.onerror = function() {
  console.error(xhr.responseText);
};
xhr.open('GET','https://www.zerocho.com/api/get'); // 메서드와 주소 설정
xhr.send(); // 요청 전송
```



### data attribute와 dataset

- 노드를 웹 서버로 사용하는 경우, 클라이언트(프런트엔드)와 빈번하게 데이터를 주고받게 되는데 가장 중요한 것은 **보안**이다.
- 프론트엔드에 민감한 데이터를 내려보내면 실수이다. 특히 비밀번호는 절대!
- HTML과 관련된 데이터를 저장하는 공식적인 방법
- 화면에 나타나지는 않지만 웹 애플리케이션 구동에 필요한 데이터들이며, 나중에 이 데이터들을 사용해 서버에 요청을 보내게 됨

```html
<ul>
    <li data-id="1" data-user-job="programmer">Zero</li>
    <li data-id="2" data-user-job="designer">Nero</li>
    <li data-id="3" data-user-job="programmer">Hero</li>
    <li data-id="4" data-user-job="ceo">Kero</li>
</ul>
<script>
    console.log(document.querySelector('li').dataset); 
    // { id:'1', userJob:'programmer' }
</script>
```

- 반대로 dataset에 데이터를 넣어도 HTML 태그에 반영됨

```html
<ul>
  <li data-id="1" data-user-job="programmer">Zero</li>
  <li data-id="2" data-user-job="designer">Nero</li>
  <li data-id="3" data-user-job="programmer">Hero</li>
  <li data-id="4" data-user-job="ceo">Kero</li>
</ul>
<p class="month">month</p>
<script>
  console.log(document.querySelector('li').dataset); 
  document.querySelector('.month').dataset.monthSalary = 10000;
  // { id:'1', userJob:'programmer' }
  // <p class="month" data-month-salary="10000">month</p>
</script>


```











