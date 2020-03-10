# SCSS



## What is the SCSS?

CSS Preprocessor는 CSS가 동작하기 이전에 사용되며, 웹에서는 CSS로 작동한다. SCSS를 통해서 불필요한 선택자의 사용, 연산 기능의 한계, 구문의 부재 등을 해결할 수 있다.

> SCSS는 웹을 디자인하기 위한 언어인 CSS에 힘과 우아함을 더 해준다.

### SCSS 작동 방법

웹에서는 CSS만 동작하므로 전처리기를 직접 동작시킬 수 없다. 그렇기에 우선 SCSS(전처리기)로 코딩하고, CSS로 컴파일 합니다. 



## Table of Contents

1. [Types](#types)

1. [중첩(Nesting)](#중첩(Nesting))

1. [Ampersand](#Ampersand)

1. [참고 문헌](#참고-문헌)

   

---



## 중첩(Nesting)

SCSS는 중첩기능을 통해 아래와 같은 이점을 얻는다.

- 부모 선택자를 반복하지 않고 작성
- 구조적으로 CSS를 작성

```scss
.section {
  width: 100%;
  .list {
    padding: 20px;
    li {
      float: left;
    }
  }
}
```

컴파일하면 아래처럼 나옴..!

```css
.section {width: 100%;}
.list {padding: 20px;}
li {float: left;}
```

## Ampersand

Ampersand(상위 선택자 참조)

```scss
.btn {
  position: absolute;
  &.active {
    color: red;
  }
}
.list {
  li {
    &:last-child {
      margin-right: 0;
    }
  }
}
```

```css
.btn {position: absolute;}
.btn.active {color: red;}
.list li:last-child {margin-right: 0;}
```



## 중첩된 속성

```scss
.box {
  font: {
    weight: bold;
    size: 10px;
    family: sans-serif;
  }
  margin: {
    top: 10px;
    left: 20px;
  }
  padding: {
	  bottom: 40px;
    right: 30px;
  }
}
```

Compiled to:

```css
.box {
	font-weight: bold;
  font-size: 10px;
  font-family: sans-serif;
  
  margin-top: 10px;
  margin-left: 20px;
  
  padding-bottom: 40px;
  padding-right: 30px;
}
```



## 변수(Variables)

반복적으로 사용되는 값을 변수로 지정할 수 있으며, 사용하기 위해선 변수의 이름 앞에 `$`를 붙인다.

```scss
$color-primary: #e96900;
$url-images: "/assets/images/";
$w: 200px;

.box {
  width: $w;
  margin-left: $w;
  background: $color-primary url($url-images + "bg.jpg")
}
```

Complied to: 

```css
.box {
  width: 200px;
  margin-left: 200px;
  background: #e96900 url( "/assets/images/bg.jpg")
}
```













## 참고 문헌

[heropy님 - Sass(SCSS) 완전 정복!](https://heropy.blog/2018/01/31/sass/)