# Typescript



타입스크립트는 자바스크립트의 상위집합(Superset)으로 자바스크립트를 포함하고 있다. 

타입스크립트가 중요하게 제공하는 기능 중 하나는 **정적타입**이다. 

타입스크립트 확장자를 가진 `.ts` 파일을 컴파일하면, `.js`파일이 생성되고, 컴파일 시점에 타입을 체크한다.

타입스크립트를 사용하면 자바스크립트도 IDE나 VScode의 도움을 받아 객체지향 프로그래밍을 좀 더 손쉽게 할 수 있고, 생산성을 높일 수 있다.



## Table of Contents

1. [Primitive Types](#Primitive-Types)
1. [DOM 탐색](#DOM-탐색)
1. [생성자](#생성자)
1. [To Do List](./ToDoList.md)

---



## Primitive Types



### Boolean(논리)

```typescript
let hasDuplicate: boolean = false;
let isDone: boolean = true;
```

### Number(숫자)

```typescript
let demical: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

### String(문자열)

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

#### generic array

`Array<elemType>`  과 같은 문법을 통해 들어올 데이터 타입을 미리 지정할 수 있다.

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
console.log(color)
```

### Any(임의)

```typescript
let sure: any = 1;
sure = "This is string";
sure = true;
```

### Void

```typescript
function log(msg): void {
  console.log("Log message: " + msg);
}
```

### Null and Undefined

```typescript
let u: undefined = undefined;
let n: null = null;
```

### Naver

```typescript
function error(message: string): never {
  throw new Error(message);
}
```



### Object(객체)

```typescript
let user: { name: string, age: number; } = {name: "ham", age:1 };
console.log(user.name);
```



**[⬆ back to top](#table-of-contents)**









