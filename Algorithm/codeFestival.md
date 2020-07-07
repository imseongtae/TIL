# JS Code Festival



## table of contents





---



## 1 ~ 50



### 문제1: 배열의 삭제

다음 배열에서 400, 500을 삭제하는 code를 입력하세요

```js
var nums = [100, 200, 300, 400, 500];
// ---result---
const ham = nums.filter(num => num < 400);
console.log(ham);
```



### 문제2: 배열의 내장 함수

pass 부분에 arr 함수가 아래처럼 출력되는 코드 구현하기

```js
// 데이터
var arr = [200, 100, 300]
// pass
// [200, 100, 10000, 300] <- 요구되는 출력값
console.log(arr);
```



```js
var arr = [200, 100, 300]
const index = arr.indexOf(300)
arr.splice(index, 1, ...[10000, 300])

```



### 문제3, 4: 변수의 타입

출력되는 변수의 타입은?

```js
var arr = [100, 200, 300]
console.log(typeof(arr))
console.log('object', typeof arr) // 나는 object라고 생각함
```



```js
var a = 1 // number
var a = 2.22 // number
var a = 'p' // string
var a = [1, 2] // object
console.log(typeof a)
```



### 문제5: for문 계산

다음 코드의 출력 값은?

```js
var a = 10;
var b = 2;

for (let i = 0; i < array.length; i++) {
  a += i // a += 1;
}

console.log(a + b);
// ---result---
// 나는 16으로 예측했으나 값이 계속 14로 나와서.. 식겁..
// 디버거로 확인해보니..! 더하기 할당 연산자에 i값이 아닌 1을 계속 넣고 있었음.
// 결국은 오타

```



### 문제6: False

자바스크립트에서 False로 취급하지 않는 것 찾기

```js
// NaN, 1, "", 0, undefined
var checkTrue = NaN;

if (checkTrue) {
  console.log('this value is the True!!')
} else {
  console.log('false!!')
}
```



### 문제7: 변수명

변수명으로 사용할 수 없는 것들 2개 고르기

- 여기서 소름돋는 결과를 얻을 수 있다... let의 함정..

```js
age
&age
let 
_age
1age

// let is disallowed as a lexically bound name
```



### 문제8: 객체의 키 이름 중복

자바스크립트의 객체를 다음과 같이 만들었다. 출력값을 입력하시오

```js
var d = {
  'weight': 78,
  'weight': 84
}
// console.log(d.weight);
console.log(d['weight']);
```



### 문제9: concat을 활용한 출력 방법

```js
var year = '2019';
var month = '04';
var day = '26';
var hour = '11';
var minute = '34';
var second = '27';
const colon = ':';
const space = ' ';

var result; // 날짜와 시간을 출력하시오

// ---result---
var result = year.concat(month, day, space, hour, colon, minute, colon, second);
console.log(result);
```



### 문제 10: 별찍기

```js
// 입력 
5

// 출력
    *   
   ***
  *****
 *******
*********

```







### 문제11: for의 기본 활용

1부터 100까지 모두 더하는 code를 <pass> 부분에 완성하기

```js
let s = 0;
// pass
console.log(s);

//---resuls---
for (let i = 0; i < 101; i++) {
	s += i;
}
```



### 문제12: 게임 캐릭터 클래스 만들기

- 게임 캐릭터 능력치와 파이어볼이 출력되게 만드시오. 

```js
// 여기 클래스르 작성하기

const x = new Wizard(545, 210, 10);
console.log(x.health, x.mana, x.armor);
x.attack();

// 출력
// 545, 210, 10
// 파이어볼
```



```js
class Wizard {
	constructor(health, mana, armor) {
		this.health = health;
		this.mana = mana;
		this.armor = armor;
	}
	attack() {
		console.log('파이어볼');
	}
}
```



### 문제13: 몇 번째 행성인가요?

- 입력으로 행성의 순서를 나타내는 숫자 n이 입력될 때 출력으로 그 순서에 해당하는 행성의 이름을 출력하기

```js
const 태양계 = [
	'수성',
	'금성',
	'지구',
	'화성',
	'목성',
	'토성',
	'천왕성',
	'해왕성',
];

const checkPlanet = n => {
	return 태양계[n - 1];
};

console.log(checkPlanet(2));

// 입출력
// 입력: 1
// 출력: 수성

```











