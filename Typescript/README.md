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
1. 
1. 

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







