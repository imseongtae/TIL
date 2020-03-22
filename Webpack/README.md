# Webpack



## Table of Contents

1. [Webpack이란?](#Webpack이란?)
1. 

---



## Webpack이란?

- 여러 파일을 하나로 합치고, 요청을 한 번만 보내기 때문에 네트워크의 `requests`를 줄이는 효과가 있다.
- 브라우저를 위한 사전 컴파일러
- 웹 페이지를 구성하는 모든 자원과 관련된 도구이다



### Webpack의 역할: 최적화

- 웹 개발 후 압축해야함
- Linter를 통해 에러 없는 방향으로 작성
- 모든 브라우저에 호환가능한 js형태로 변환..!
- CSS 최적화
- img 최적화

### Webpack의 모드 3가지
- development
- production
- none: "webpack --mode=none"

#### webpack.config.js
`webpack.config.js`를 통해 
build 명령어를 통해 실행하는 webpack의 모드를 설정할 수 있다.

```javascript
// common.js 모듈 문법
module.exports = {
  mode: 'none',
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist') // 첫 번째 인자 폴더 주소 기준
  }
};
```



### Webpack build 파일 분석
- 1 ~85번까지 webpack 내부관련 로직(살펴볼 필요가 없음)
- 87 ~ IIFE(끝까지 Immediately Invoked Function Expression)임

### 다른 웹 테스크 매니저와의 차이점
- 진입점이 하나이다.!







## 참고자료

- [웹팩 핸드북](https://joshua1988.github.io/webpack-guide/)