# JavaScript


## table of contents


---



## Methods 정리

```js
const number = parseInt('1234hello', 10) // 1234


```


### stack
LIFO(Last In First Out)

```js
const arr = [];
arr.pop(); // 배열의 개수 리턴

arr.push(); // 배열의 개수 리턴
```


### queue

```js
const arr = [2, 4, 8];

arr.shift(); // 2 를 출력하고, 배열의 길이가 2가됨
arr.unshift(3); // 3을 배열 첫번째 자리에 입력
```




### flat
flat을 통해 배열을 한꺼풀 벗겨냄
몇차원의 배열이든 1차원 `Array`로 만들어줌

```js
const arrThree = [1,2,3,[4,5,[6,7,8,9]]] 
// Array(4) [ 1, 2, 3, (3) […] ]

arrThree.flat();
// Array(6) [ 1, 2, 3, 4, 5, (4) […] ]

arrThree.flat(2);
// Array(9) [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]

```

### includes

```js
const arr = [ 10, 2, 4, 8 ];

arr.includes(1) // false
arr.includes(10) // true

```

### join

배열을 특정 문자열을 기준으로 합칠 때

```js
const arr = [ 10, 2, 4, 8 ];
arr.join('!')
// "10!2!4!8"
```


### splice와 slice
- `splice`: 배열의 요소를 삭제하거나 교체할 때
- `slice` : 요소를 인덱스 기준으로 잘라낼 때

```js
const arr = [ 10, 2, 4, 8 ];

arr.splice(0, 1) // 10
arr // 2, 4, 8

arr.splice(0, 2, [10, 2]) // [ (2) […], 4, 8 ]
arr.flat(); // [ 10, 2, 4, 8 ]


```




## Set 
- 중복을 제거할 때 사용하기도 한다.
- `Set`의 length를 구하고 싶을 때는 `size` 프로퍼티를 사용한다.

```js

let ham = [1,1,1,1,1,1,1,3,3,3,3,3,2,2,2,2,4,5]
const s = new Set(ham)
console.log(s) // [1,3,2,4,5]

s.size // 5
s.has(1); // true

```


## String

- 정규표현식의 사용을 더 높여서 생산성을 높이자
- 정규표현식 match API를 통해 할 수 있는 일이 정말 많아질 것 같다.

```js
let str = 'abc abc abc de de abcde defg ABC'
console.log(str) // "abc abc abc de de abcde defg ABC"

str.concat('hello word')

str.includes('fgh') // false
str.includes('abc') // true

str.split(' ') // [ "abc", "abc", "abc", "de", "de", "abcde", "defg", "ABC" ]

// global과 대소문자 적용 정규 표현식
str.replace(/abc/g, '!') // "! ! ! de de !de defg ABC"
str.replace(/abc/gi, '!') // "! ! ! de de !de defg !"

str.replace(/ /g, '-') // "abc-abc-abc-de-de-abcde-defg-ABC"

str.indexOf('abcde') // 18
str.slice(18, 23) // "abcde"

str.length // 32

str.match(/abc/g) // Array(4) [ "abc", "abc", "abc", "abc" ]

```