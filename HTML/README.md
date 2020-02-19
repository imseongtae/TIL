# HTML



## Table of Contents



1. [시멘틱 태그](#시멘틱-태그)
5. [WAI-ARIA](#WAI-ARIA)
1. [DOM 탐색](#DOM-탐색)
1. [생성자](#생성자)
1. [class](#class)
1. [Destructuring](#destructuring)

---



## 시멘틱 태그 

시멘틱 태그는 브라우저, 검색엔진, 개발자에게 콘텐츠의 의미를 명확히 설명하는 역할을 한다. 시맨틱 태그를 통해 컴퓨가 HTML 요소의 의미를 명확히 해석하고 그 데이터를 활용하는 시멘틱 웹이 실현될 수 있다.

> 시맨틱 웹이란 웹에 존재하는 수많은 웹페이지에 메타데이터(Metadata)를 부여하여, 기존의 잡다한 데이터 집합이었던 웹페이지를 ‘의미’와 ‘관련성’을 가지는 거대한 데이터베이스로 구축하고자 하는 발상이다.

**더 자세한 이야기는 참고문헌**을 통해

- SEO의 목적

- 검색 엔진은 로봇을 통해 웹사이트의 정보를 수집

  

### 개발자가 얻는 이점

#### non-semantic 태그로 작성한 구조

```html
<div id="header">
  
</div>

<div id="container">
  <div class="article-setion">
  	<h2>내용의 제목</h2>
  </div>
  
</div>

<div id="footer">
  
</div>
```

#### semantic 태그로 작성한 구조

```html
<header>
	<!-- 제목, 로고, 목차  -->
</header>

<main>
  <section>
  	<h2>내용의 제목</h2>
  </section>

</main>

<footer>
	<!-- 하단 정보, 저작권  -->
</footer>
```

**개발자는 시멘틱 태그의 사용을 통해 코드의 가독성을 높이고 유지보수를 쉽게할 수 있는 장점을 얻는다.**

Vue에서 컴포넌트를 통해 각각의 역할과 기능을 분리했듯이 시멘틱 태그를 통해서 문서의 구조와 의미를 나눌 수 있다. 

아래는 HTML5에서 새롭게 추가된 시멘틱 태그이다.

| tag     | Description                                          |
| :------ | :--------------------------------------------------- |
| header  | 헤더를 의미한다                                      |
| nav     | 내비게이션을 의미한다                                |
| aside   | 사이드에 위치하는 공간을 의미한다                    |
| section | 본문의 여러 내용(article)을 포함하는 공간을 의미한다 |
| article | 분문의 주내용이 들어가는 공간을 의미한다             |
| footer  | 푸터를 의미한다                                      |

**[⬆ back to top](#table-of-contents)**



## WAI-ARIA

초기의 웹은 문서 간의 연결을 위한 목적으로 설계되었지만 기술의 발전으로 인해 웹은 데스크탑 애플리케이션과 같은 수준의 사용자 경험을 요구하기에 이르렀다.

### RIA(Rich Internet Application)

Javascript의 성장과 Ajax의 등을 통해서 웹에서 데스크탑 수준의 애플리케이션과 같은 사용자 경험을 제공할 수 있게 되었고,  RIA를 등장시켰다.  RIA의 등장은 역동적이고 화려하며 편리한 UX를 제공하지만 모든 사용자가 동등하게 접근할 수 없는 문제가 생긴다.

장애인, 정보 접근 약자들은 스크린 리더 등 보조기술을 사용하더라도 RIA기술로 제작된 웹 애플리케이션을 제대로 사용할 수 없는 문제가 생긴다.

### WAI-ARIA (Web Accessibility Initiative - Web Accessible Rich Internet Applications)

W3C에서 웹 콘텐츠 및 웹 애플리케이션의 접근성을 개선하기 위한 명세인 **WAI-ARIA** 발표했다. **WAI-ARIA**는 마크업에 역할, 속성, 상태의 정보를 추가할 수 있도록 지원한다. 

- 역할(Role) - 유저 인터페이스에 포함된 특정 컴포넌트의 역할을 정의
- 속성(Property) - 해당 컴포넌트의 특징이나 상황을 정의하며 속성명으로 `"aria-*"`라는 접두사를 사용
- 상태(State) - 해당 컴포넌트의 상태 정보를 정의 

### WAI-ARIA Role

**역할은 특정 요소에 기능을 정의하는 것을 말한다.**

키보드 초점을 받을 수 있는 a태그는 다양한 용도로 사용되기도 하는 데, 컴포넌트 구현을 위해 a태그를 버튼으로 사용할 경우 스크린리더 사용자에게 혼란을 줄 수 있다. 이를 해소하기 위해 a태그에 `role="button"` 속성을 지정하면 스크린리더는 버튼이라고 읽어주어 사용자에게 태그의 의미가 아닌, 목적에 맞는 의미를 전달할 수 있다.

```html
<a href="/" onclick="playApp()" role="button">재생</a>
```

WAI-ARIA Role은 다음 4가지의 카테고리로 구분할 수 있다.

- 문서구조 역할(Document Structure Role)
- 추상 역할(Abstract Role)
- 랜드마크 역할(Landmark Role)
- 위젯 역할(Widget Role)

### WAI-ARIA Property 

속성(Property )은 `Elment`가 기본적으로 갖고 있는 특징이나 상황을 의미한다. 

> 폼의 입력 상자가 읽기 전용(readonly)인지, 또는 필수 항목(require)인지, 사용자 입력에 대해 자동 완성(auto Complete) 기능을 지원할 지 또는 드래그(drag)가 가능한지, 팝업(has popup)이 뜨는지, 업데이트된(live) 정보가 있는지 등의 상황을 사용자가 인지할 수 있도록 한다.

속성의 예로 입력 폼을 들 수 있다. 회원가입 시 사용자에게 아이디와 비밀번호를 입력받아야 하며, 해당 입력 값이 필수 항목일 경우 입력 상자에 `aria-required="true"`를 통해 스크린리더 등의 보조기기에서 해당 항목이 필수 항목임을 알 수 있도록 제공할 수 있다. 

```html
<div class="id-area">
  <label for="user-email">아이디</label>
  <input type="email" id="user-email" aria-required="true">
</div>
<div class="pw-area">
  <label for="user-pw">비밀번호</label>
  <input type="password" id="user-pw" aria-required="true">
</div>
```



### WAI-ARIA State

상태(State)는 요소의 현재 상태를 의미하며, 상황의 변화에 따른 값을 가진다. 

> 메뉴가 펼쳐진 상태(expanded)인지, 적절하지 못한(invalid) 값이 입력되었는지, 콘텐츠가 숨김(hidden) 상태인지 등을 나타낼 수 있다.

가령, 애플리케이션에서 제공되는 메뉴가 하위 메뉴를 포함하고 있을 경우, 현재 하위 메뉴가 접힌 상태인지 펼쳐진 상태인지 스크린 리더 사용자에게 정보를 제공해야 할 경우가 있다. 이 때 `aria-expanded="false"` 속성을 통해 하위 메뉴가 접힌 상태라면 `false`, 값을 펼친 상태라면 `true` 값을 지정할 수 있다.

```html
<ul id="menu" role="tree">
  <li>
  	<a>WAI-ARIA</a>
    <ul id="sub-menu" role="group">
      <li id="menu" role="treeitem" aria-expanded="false">
      	<a>WAI-ARIA 란?</a>
      </li>
    </ul>
  </li>
  <li id="menu" role="treeitem" aria-expanded="false">
  	<a>WAI-ARIA의 목적</a>
  </li>
</ul>
```



### aria-hidden

```vue
<span class="addContainer" v-on:click="addTodo">
	<i class="fa fa-plus" aria-hidden="true"></i>
</span>
```

HTML 태그에 `aria-hidden="true"`를 지정하면 스크린 리더 등의 보조기기에서 의미적으로 숨긴 콘텐츠로 인식하여, 스크린 리더의 가상 커서로 요소를 탐색할 수 없게 된다.

| 속성  | 의미                                                         |
| ----- | ------------------------------------------------------------ |
| true  | 스크린 리더와 같은 보조기술 사용자의 콘텐츠 탐색을 제한하며, 가상 커서에 탐색되지 않음 |
| false | 스크린 리더 같은 보조기술 사용자에게 숨겨진 콘텐츠를 노출하여, 가상 커서를 통한 탐색을 허용 |

**[⬆ back to top](#table-of-contents)**



### 랜드마크

`HTML5`에서 새롭게 추가된 섹션 관련 요소의 경우 `WAI-ARIA` 규칙과 동일한 역할의 요소가 다수 있다. **W3C**에서는 `HTML5` 섹션 관련 요소와 `WAI-ARIA` 규칙을 함께 사용할 경우 해당 기능이 무효화되거나 충돌이 발생할 수 있으므로 중복해서 사용하지 않도록 당부하고 있다.

| Landmark Role      | HTML5 섹션 관련 요소                                         |
| ------------------ | :----------------------------------------------------------- |
| role="application" | 동일한 역할의 요소가 없음. 주로 `<div>`요소와 같이 그룹 역할을 하는 요소로 대체할 수 있다. |
| role="main"        | 본문의 주요 콘텐츠 영역으로 한 페이지 내에 1개만 사용 가능하며 `<article>`, `<aside>`, `<footer>` 요소의 하위 요소로 사용할 수 없다. |
| role="search"      | 동일한 역할의 요소가 없음. 검색의 역할을 담당하는 서식을 의미하며 `<div>`또는 `<form>` 요소의 사용을 권장한다. |







## 참고 문헌

- [시맨틱 요소와 검색 엔진 - poiemaweb](https://poiemaweb.com/html5-semantic-web)
- 웹 접근성 연구소

**[⬆ back to top](#table-of-contents)**