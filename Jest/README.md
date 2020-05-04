# Jest

## 프론트 엔드 테스팅

특정 기능을 테스트하는 코드를 작성하기 위한 기능

## 테스팅

### 테스팅 환경 구성

1. `jest.config.js`  파일에 속성 추가 
2. 기본적으로 vue-cli 로 생성했을 때 잡히는 package.json의 scripts에 test:util로 잡히는 명령어를 test로 수정하고 `--watchAll` 속성 추가. 이렇게 하면 자바스크립트 테스팅이 기본적으로 jest로 설정되어 있는데, jest 라고 설정된 도구에서 테스트 코드를 실행할 때 `--watchAll`  이라는 옵션을 붙여서 테스트 코드 파일이 변화되었을 때마다 자동으로 다시 테스트 코드를 실행해주는 명령이 됨

- `jest.config.js` 파일에 속성 추가

- 기본적으로 vue-cli 로 생성했을 때 잡히는 `package.json`의 scripts에 `test` 명령어 수정

**테스트 코드 파일은 가급적이면 대상이 되는 파일과 가까운 위치에 생성해야 한다!** (test 코드를 작성하는 폴더 안에만 테스팅 파일을 모아놓는 방법 등 여러 규칙이 있을 수 있지만 판교님은 이 규칙을 따름)

- `LoginForm.vue`파일을 테스팅하는  `LoginForm.spec.js` 테스트 파일 생성
- `npm t` 명령어를 입력하면 `package.json` 에서 설정했던 명령어에 따라서 테스트 코드가 실행됨

```jsx
// LoginForm.spec.js 생성

```

```jsx
npm t // 까지만 입력하면 테스트 코드가 실행되나. 
```

   

### 테스트 코드가 필요한 이유

**테스팅의 목적은 일일히 기능을 손으로 확인하는 시간을 줄이는 데** 있다.(직접 값을 입력하고 확인하며, 테스트하는 시간을 줄일 수 있음)

가령, 로그인 페이지의 목적은 로그인 눌렀을 때 권한을 주고 다음 페이지로 이동해야하는 기능이다.

1. id 인풋박스에 이메일을 입력했을 때 이메일이 맞는지 확인하는 로직
2. id, pw 가 맞는 경우 로그인 처리를 진행하고 다음 페이지로 이동

로그인 기능을 테스트하기 위해 다양한 값들을 넣어보면서 validation문구가 뜨는지 확인해야 한다.

![example](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46d36f9b-fed9-4cca-877b-9ec0c642f054/Untitled.png)

## Jest

### Jest 소개

가장 높은 만족감을 기록중인 Jest..! 높은 사용률을 점유하고 있음 만족감이나 관심도가 다른 테스팅 라이브러리에 비해서 월등히 높음

1. Docs가 굉장히 잘 만들어져 있음, 페이스북이 관리하고 있음
2. 


### Jest 설치

`vue-cli` 로 프로젝트를 생성할 당시 이미 테스트 라이브러리로 `Jest`를 선택한 경우라면 굳이 설치할 필요가 없다. 설치해야 한다면 아래처럼 설치

```jsx
$ npm install --save-dev jest
$ yarn add --dev jest
```

## 학습하며 느낀 점

## 참고 자료

[The State of JavaScript 2019: Testing](https://2019.stateofjs.com/testing/)