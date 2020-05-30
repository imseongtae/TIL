# Figma

브라우저에 기반해 프로그램이 실행되므로 Sketch와는 다르게 OS에 종속되지 않는다.그리고 실시간으로 협업이 가능하다. 이러한 강점으로 인해 현재 UX/UI툴 3대장 중에 하나이다. 

## Table of Contents

1. [단축키](#단축키)
1. [Skill](#Skill)
1. [Frame](#Frame)
1. [Grid System](#Grid-System)
1. [작업물](#작업물)
1. [참고문헌](#참고문헌)



---





## 단축키

- `ctrl`을 누르고 마우스로 할 수 있는 일이 많다!
- `alt`를 통해 간격을 잡을 수 있다. 

| 단축키        | 기능               |
| ------------- | ------------------ |
| 잠그기        | `ctrl + shift + L` |
| 그룹화        | `ctrl + G`         |
| 이름 변경     | `ctrl + R`         |
| 컴포넌트 생성 | `ctrl + alt + k`   |
| Rectangle     | `R`                |
| Arrow         | `shift + L`        |
|               |                    |
|               |                    |



## Skill

### Figma로 프로젝트 세팅하는 법

1. 디바이스를 고려하여 Frame(혹은 아트보드)의 사이즈 결정
2. 보기 배율을 100%로 설정 - **가장 중요한 설정**이므로 100번 강조해도 아깝지 않음
3. 일관된 디자인을 위해 그리드 시스템을 설정. 단, 모바일이라면 좌우 여백(마진)을 통해 그리드 시스템을 대신한다. 여백 값은 16, 24, 32 등 8의 배수로 선택한다
4. 기본 문단의 폰트 사이즈를 16px로 설정하고, 이를 기준으로 title, nav 등의 사이즈를 찾아나간다
5. 색상을 결정하고, 웹 접근성 기준에 적합한 명도 대비(4.5 : 1)을 맞춘다.

### Figma에서 명도 대비 맞추는 법

![image](https://user-images.githubusercontent.com/60806840/83334765-bff4f880-a2e3-11ea-8f23-a928f307c08d.png)

- Able 플러그인을 켜놓고 두 개의 레이어를 같이 선택하면 선택한 두 요소의 대비가 좋은지 나쁜지 등급을 확인할 수 있다. 
- WCAG는 텍스트 또는 이미지 텍스트의 시각적인 표현은 다음 예외사항을 제외하고 명도 대비 차(contrast ratio)는 최소 4.5:1이 되어야 한다고 권고한다.
  - 큰 텍스트: 24px 이상 또는 18px Bold 텍스트의 경우 3:1 명도 대비 차까지 허용
  - 중요하지 않은 요소: 비 활성화된 [UI 컴포넌트](https://www.w3.org/TR/WCAG21/#dfn-user-interface-components) 텍스트나 이미지의 텍스트, [순수한 표현 장식](https://www.w3.org/TR/WCAG21/#dfn-pure-decoration), 보이지 않는 콘텐츠 등
  - 로고타입(Logotypes): 로고나 브랜드의 텍스트는 최소한의 명도 대비 요구가 없음



### Fill Linear

- Linear 속성을 이용해 세련미 있는 디자인을 만들 수 있다. 
- 



## Frame

- 웹 디자인을 꼼꼼하게 작업해야 한다면 breakpoint를 고려하여 대응할 해상도별 Frame을 늘어놓고, 페이지 단위로 묶어서 작업해나간다.

-  `Frame`을 `1080 or 1280` 부터 시작해  `1600 or 1980` 으로 설정한다.

- 

  

## Grid System

오브젝트와 오브젝트 사이를 조정하여 디자인의 레이아웃에 규칙을 부여하는 수단이며, Grid System 규칙을 따르면 자동으로보다 일관된 UI를 얻게 된다. Grid System은 칼럼(Column), 거터(Gutter),  마진(Margin) 세 가지 요소로 구성된다.

- 웹 다지인의 경우에는 12그리드 시스템을 많이 사용하며, Gutter 값은 기본값 20으로 진행 

## 작업물

- [Design Tutorial A Music Website](https://www.figma.com/file/aFhCvX8lElRxuY2cW1QXV0/Untitled?node-id=0%3A1)





## 참고문헌

- [FIGMACRUSH - Figma UI kits, Templates & Freebies](https://www.figmacrush.com/)
- [Figma Premium Responsive UI Kit](https://www.figmacrush.com/neolex-figma-premium-ui-kit/)
- [Figma DB](https://www.notion.so/Figma-DB-1a16657816834e3c85da874ea788e8a2)
- [개발자도 알면 좋은 UI 디자인 - 캡틴판교](https://joshua1988.github.io/web-development/design/ui-for-developers/)
- [7 web design styles you need to know](https://www.booklets.io/b/7-web-design-styles-you-need-to-know-ransegall)
- [WCAG 2.1 - 명료성](https://yamoo9.gitbook.io/wcag/1-perceivable/1.4-distinguishable#1-4-3-aa)





