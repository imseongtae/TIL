# TypeScript

## What is the TypeScript?

타입스크립트는 자바스크립트의 상위집합(Superset)으로 
자바스크립트를 포함하고 있는 프로그래밍 언어이다.

타입스크립트가 중요하게 제공하는 기능 중 하나는 **정적타입**이다. 
변수, 함수 매개변수, 함수 리턴값에 타입이 명시적으로 붙어서 약한 타입의 Javascript를 강한 타입으로 만들어 주는데, 이는 다음과 같은 이점을 가져다 준다.

1. 안정적이고
1. 에러가 적게 발생하며
1. IDE 및 VSCode의 지원을 받을 수 있게 된다. 

> TypeScript와 VSCode 모두 MS에서 만들어 호환이 잘 된다. 때문에 에디터 없이 TypeScript를 사용하면 TypeScript가 가지는 이점이 다 사라진다. 타입을 외워서 감으로 한다는 것(머리속으로 한다는 것)은 js에서 ts로 전환하는 생산성이 떨어진다.

TypeScript를 사용하면 Javascript도 IDE나 VScode의 도움을 받아 객체지향 프로그래밍을 좀 더 손쉽게 할 수 있고, 생산성을 높일 수 있다.

### TypeScript의 컴파일

타입스크립트 확장자를 가진 `.ts` 파일을 컴파일하면, `.js`파일이 생성되고, 컴파일 시점에 타입을 체크한다.

TypeScript는 `Compile(컴파일)`이라는 개념이 나온다. TypeScript는 언어이자 라이브러리이다. 언어는 실행기가 있어야 하는데, Javascript는 대표적으로 브라우저와 Node.js 라는 실행기가 있다.

> 짚고 넘어가자면 Node.js는 서버가 아니라 자바스크립트 실행기이다. 브라우저도 메인 기능은 아니지만.. Javascript 엔진이 있으므로 실행기이다.



TypeScript를 실행하기 위해선 TypeScript룰 컴파일해주는 Node.js가 필요하다. 이러한 이유로 TypeScript 학습을 위해선 Node.js에 대한 이해도 어느 정도 필요하다



## Table of Contents

1. [Primitive Types](#Primitive-Types)
1. [Type alias](#Type-alias)
1. [Function](#Function)
1. [Interface](#Interface)
1. [Class](#Class)
1. [Generics](#Generics)
1. [Inheritance](#Inheritance)
1. [Access modifier](#Access-modifier)
1. [getter/setter](#getter/setter)
1. 

---



## Primitive Types

### Boolean(논리)

```typescript
let hasDuplicate: boolean = false;
let isDone: boolean = true;
```

### Number(숫자)

자바스크립트와 마찬가지로 모든 숫자를 부동소수점으로 나타냄. 

```typescript
let demical: number = 6;
let hex: number = 0xf00d; // 16진수
let binary: number = 0b1010; // 2진수
let octal: number = 0o744; // 8진수
```

### String(문자열)

따옴표와 쌍따옴표를 사용

```typescript
let color: string = "blue";
color = 'red';
```

```typescript
let fullName: string = "Hong Gildong";
let sentence: string = `Hello, my name is ${fullName}`;
```

### Array(배열)

같은 타입으로만 이루어진 배열을 넣는 방법

```typescript
let list: number[] = [1,2,3];
```

#### **generic array**

`Array<elemType>`과 같은 문법을 통해 들어올 **데이터 타입**을 **미리 지정**할 수 있다.

```typescript
let list Array<number> = [1,2,3];
```

### Tuple(튜플)

요소에 다양한 타입이  올 수 있는 배열 타입

```typescript
let x: [string, number];
x = ["x", 10];
x = [10, "x"]; // Error
```

### Enum(열거)

```typescript
enum Color { Red = 1, Green, Blue }
let color: Color = Color.Green;
console.log(color) // 2
```

### Any(임의)

동적 콘텐츠가 컴파일 타입검사를 통과하도록 해줌, 다만 임의형을 자주 사용하게 되면 정적 변수를 사용하는 게 무의미해진다. 

```typescript
let sure: any = 1;
sure = "This is string";
sure = true;
```

### Void

어떤 것도 없다는 의미, 값을 반환하지 않는 함수의 반환 유형으로 쓰임

```typescript
function log(msg): void {
  console.log("Log message: " + msg);
}
```

### Null and Undefined

다른 모든 타입의 하위타입. 모든 타입에 null과 undefined를 지정할 수 있음

```typescript
let u: undefined = undefined;
let n: null = null;
```

### Never

절대 발생하지 않을 값의 유형을 나타냄. 절대 리턴이 발생하지 않는다든가, 항상 예외값을 던져 절대 반환을 하지 않는 경우

```typescript
function error(message: string): never {
  throw new Error(message);
}
function forever(): never {
  while(true) {
    
  }
}
```



### Object(객체)

타입으로 지정되지 않은 타입. 즉, number, string, symbol, null, undefined 가 아닌 다른 유형을 말한다.

```typescript
let user: { name: string, age: number; } = {name: "ham", age:1 };
console.log(user.name);
```



**[⬆ back to top](#table-of-contents)**



## Type alias

### 복잡한 타입을 간단하게 쓸 수 있는 기능

```typescript
type = UNIQID = string | null

function getUserID(id: UNIQID) {
	console.log(id)
}

getUserID('ham1234')
getUserID(null)
getUserID(12) // error TS2345: Argument of type '12' is not assignable to parameter of type 'string'.

```

### 특정값만 받는 기능

```typescript
type USER_TYPE = 'TESTER' | 'ADMIN'
let userType: USER_TYPE = 'TESTER'
userType = 'abcd' // Type '"abcd"' is not assignable to type 'USER_TYPE'.
```



## Function

함수 선언문과 함수 리터럴로 정의하는 방법을 모두 사용할 수 있다. 

```typescript
const Add = function(a: number, b: number): number {
  return a + b;
}
```

### 파라미터는 기본값을 넣어줄 수도 있고, 넣지 않을 수도 있다.

```typescript
function point(x:number, y:number = 10): number {
	return x + y;
}
console.log("OUTPUT: " + point(20)) // OUTPUT: 30

function optionPoint(x: number, y?: number): number {
  if(y) {
    return x + y;
  }
  return x;
}
console.log("OUTPUT: " + optionPoint(10, 10)) // OUTPUT: 20
console.log("OUTPUT: " + optionPoint(10)) // OUTPUT: 10

```

### rest Parameter

```typescript
function cities(name: string, ...restName: string[]) {
  return name+ ',' + restName.join(',')
}

let ourCities = cities('서울', '경기', '부산', '광명', '대구', '인천', '광주')
console.log(ourCities)
```

### tsc를 통해 컴파일

```javascript
function cities(name) {
    var restName = [];
    for (var _i = 1; _i < arguments.length; _i++) {
        restName[_i - 1] = arguments[_i];
    }
    return name + ',' + restName.join(',');
}
var ourCities = cities('서울', '경기', '부산', '광명', '대구', '인천', '광주');
console.log(ourCities);
```

### example

```typescript
function sumArr(numbers: number[]): number {
  return numbers.reduce((acc, current) => acc + current, 0)
}
const total = sumArr([1,2,3,4,5]);
console.log(total) // 15
```



## Interface

> JAVA에서는 인터페이스를 아무것도 구현된 것이 없는 기본 설계도로 표현하며, 오직 추상 메서드와 상수만을 멤버로 가진다. 인터페이스는 불완전하므로 다른 클래스를 작성하는 데 도움을 줄 목적으로 사용된다. 

타입의 이름을 지정하는 역할(코드의 타입을 정의), 자바스크립트로 컴파일 될 때 제거

개념적으로 와닿지 않으면..! 사용하려는 자료형을 조립해서 사용한다고 생각하면 됨

```typescript
interface Size { width: number; height: number;}
interface Label { title: string; size: Size;}

function labelPrint(label: Label): void {
  console.log(label)
}
let myLabel = <Label>{
  title: '타입스크립트 도서', size: { width: 20, height: 29 }
}

labelPrint(myLabel)
```

`<Config>`나 `as Config`는 타입 어설션(Type assertions)의 표현식으로 같은 의미이다.

```typescript
interface Config { name: string; path: string; version?: string; }
interface App { fullPath: string; version?: string; }

function applicationInit(config: Config): App {
  let app = {fullPath: config.name + config.path} as App
  if(config.version) {
    app.version = config.version
  }
  return app;
}

console.log(applicationInit({name:'ham', path:'/til/folder'} as Config))
console.log(applicationInit(<Config>{name:'ham', path:'/til/folder', version: '1.0.0'}))
```

### example.1

`constructor`의 파라미터에 **접근 제한자**를 사용하여 **멤버 변수 사용을 대체**하기

```typescript
interface Shape {
  getArea(): number, // Shape interface에는 getArea라는 함수가 꼭 있어야 함
}

class Circle implements Shape {
  constructor(public radius: number) {
    this.radius = radius;
  }  
  getArea() { // 너비를 구하는 함수
    return this.radius * this.radius * Math.PI;
  }
}

class Rectangle implements Shape {
  height: number;
  constructor(private width: number, height: number) {
    this.width = width;
    this.height = height;
  }
  getArea() {
    return this.width * this.height;
  }
}

const shapes: Shape[] = [new Circle(5), new Rectangle(5, 10)]
shapes.forEach(shape => {
  console.log(shape.getArea()) // 78.53981633974483 // 50
})
```

### example.2

`interface`가 `interface`를 상속(`extends`)하는 예제. `interface`를 통해서 코드의 중복을 제거. `interface`를 상속하지 않았다면 `property`의 개수가 늘어남

```typescript
interface Person {
  name: string;
  age?: number;
}
interface Developer extends Person {
  skills: string[],
}
const person: Person = {
  name: '임사람',
  age: 30,
};
const expert: Developer = {
  name: '임개발',
  skills: ['JavaScript', 'TypeSript', 'Vue.js']
}
const people: Person[] = [person, expert];
console.log(people);
// [{ name: '임사람', age: 30 },{ name: '임개발', skills: [ 'JavaScript', 'TypeSript', 'Vue.js' ] }]
```



## Class

```typescript
class Animal {
  name: string;
  legs: number;

  constructor(name: string, legs: number = 4) {
    this.name = name;
    this.legs = legs;
  }
  info(): string {
    return `${this.name} has ${this.legs} legs`;
  }
}

let dog: Animal = new Animal('멍멍이')
console.log(dog.info()) // 멍멍이 has 4 legs
```



## Generics

`Generics`은 타입스크립트에서 `funtion`, `class`, `interface`, `type alias` 를 사용하게 될 때 여러 종류의 타입에 대해 호환을 맞춰야 하는 상황에서 사용. 함수에 `Generics`을 사용하면 파라미터로 다양한 타입을 넣을 수도 있고, 타입 지원을 지켜낼 수도 있습니다. 

### function에서 Generics

```typescript
function merge<A, B>(a: A, b: B): A & B {
  return {
    ...a, 
    ...b,
  }
}
const merged = merge({foo: 1}, {bar: 1})
console.log(merged) // { foo: 1, bar: 1 }
```

```typescript
function wrap<T>(param: T) {
  return {
    param
  }
}
const wrapped = wrap(10);
console.log(wrapped) // { param: 10 }
```

### Interface에서 Generics

```typescript
interface Items<T> {
  list: T[];
}
const items: Items<string> = {
  list: ['a', 'b', 'c']
}
console.log(items) // { list: [ 'a', 'b', 'c' ] }
```

### type에서 Generics

```typescript
type Items<T> = {
  list: T[];
}
const items: Items<string> = {
  list: ['one','two','three']
}
```

### class에서 Generics

```typescript
class Queue<T> {
  list: T[] = [];
  get length() {
    return this.list.length;
  }
  enqueue(item: T) {
    this.list.push(item);
  }
  dequeue() {
    return this.list.shift();
  }  
}

const queue = new Queue<number>();
queue.enqueue(0);
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);
queue.enqueue(4);
console.log(queue.dequeue()); // 0
console.log(queue.dequeue()); // 1
console.log(queue.dequeue()); // 2
console.log(queue.dequeue()); // 3
console.log(queue.dequeue()); // 4
```



## Inheritance

하위 클래스를 만들 때는 `extends` 키워드를 사용. 파생 클래스는 생성자 함수에서 `super()`를 호출해야 하며, 상위 클래스의 메서드를 호출할 수 있다.

```typescript

```



## Access modifier

### public 

```typescript
class Face {
  public edge: number;

  constructor(edge: number) {
    this.edge = edge;
  }
}

class Rect extends Face {
  constructor() {
    super(4);    
  }
}

const rect = new Rect();
console.log(rect.edge)
```

### private

### protected

### readonly



## getter/setter

`get` 키워드를 붙여 값을 받을 수 있고, `set` 키워드를 붙여서 값을 할당할 수 있다. 

```typescript
class Face {
  private _edge: number = 3;
  get edge() {
    return this._edge;
  }
  set edge(value: number) {
    this._edge = value;
  }
}
const face = new Face()
console.log(face.edge)
face.edge = 5;
console.log(face.edge)
```















