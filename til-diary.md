# Diary📒

하루를 돌아보기 위해 **TIL Diary**📒를 작성합니다. 학습 내용 및 학습하며 겪었던 어려움이나 문제 해결과정을 기록합니다. 



---





**Tue Jul 20 2020**

- [x] pcs back-end Refactoring 
- [x] `Sequelize setting`

**Mon Jul 20 2020**

- [x] web2 nodejs master branch에 `rebase`

**Sun Jul 19 2020**

- [x] API Test

**Sat Jul 18 2020**

- [x] html과 css 학습했던 내용 Github에 정리
- [x] 정리한 내용 중에 3개 포트폴리오에 포함
- [x] web2 nodejs 학습내용 정리하며, 코드 리팩토링 진행 중에 여러 에러를 겪음.. express 사용해서 CRUD API를 만드는 것과는 다른 종류의 에러

**Fri Jul 17 2020**

- [x] nodejs api 만들 때 `/` 슬래시 빼서 에러 발생. express를 사용한다면 만나지 않을 에러지만.. 새삼 URL 요청을 받는 처리의 중요성을 실감
- [x] `home` 함수에서는 파리미터 `response` 하나만 전달받아 사용하는데, home 함수를 호출하는 곳에서 `home(request, response)` 처럼 두 개의 arguments를 전달하여 에러
- [x] `form attribute`를 설정할 때 `method`를 `post`로 설정하지 않아서 에러 발생!
- [x] update나 delete 같은 작업을 요청할 때 쿼리스트링으로 id값을 전달한다. 생활코딩 강의에서는 `<input type="hidden" value={author.id} />` 처럼 `attribute`를 작성
- [x] 트랜잭션은 일련의 작업을 실패했을 때 지금까지 내렸던 명령을 한 번에 이전으로 돌릴 수 있는 환상적인 기능이다. - 이고잉샘의 설명
- [x] 저자가 삭제되었을 때, 저자가 작성했던 글 또한 연쇄적으로 삭제하기 위한 처리 작업. 가령, 저자 중 taeho가 삭제되었을 때, taeho가 작성한 글도 삭제되도록 - https://github.com/imseongtae/web2-nodejs-mysql

**Thu Jul 16 2020**

- [x] Javascript 100제 문제 풀이
- [x] `React` 복습

**Wed Jul 15 2020**

- [x] 오늘은 종일 왜 안 되는지 생각만 한 것 같.. 코딩을 해야 하는데...😫

**Tue Jul 14 2020**

- [ ] `react-native` 를 활용한 앱 개발은 실행환경이 달라 생기는 어려움과 익숙하지 않은 에러들이 많음. 이로 인해 웹 개발에 비해 재미가 떨어진다고 느낌
- [ ] `React`에도 그렇게 익숙하지도 않아서  `react-native` 학습이 어떻게 보면 허들..!이긴 하지만 확실히 리액트가 가지는 이점이 크다는 사실을 깨달음! => `react-native`를 통해서 `React` 학습에 다시 박차를 가하는 계기를 갖자

**Mon Jul 13 2020**

- [x] `react-native` 로 특정 기능을 구현하고 싶어도 기능을 특정할 수 있는 keyword를 모르겠음. 특정 기능의 이름을 모르니.. slide up, modal, dropdown의 변형 등 다양한 검색어 속에서 헤매이게 됨
- [ ] `react-native` 에서는 CSS Flex가 권장된다고 하는데, 버튼 위치를 잡을 때 `position: absolute`를 사용함.. 아직 익숙해지기 위해서는 시간이 더 필요하다는 것을 반증하는 코드..!

**Sun Jul 12 2020**

- [x] react-native todo app이 `react native version mismatch` 라는 오류를 발생하며 실행이 안 되는 오류가 발생. 이를 해결하기 위해 stackoverflow 를 살펴봤지만 이 오류를 해결할 수 있는 눈에 띄는 방법은 없었음..! `react-native` 버전을 낮추거나 높이는 시도, 모든 터미널을 닫고 다시 시작하는 시도 등은 의미가 없었고, `node_modules` 을 지우고 다시 실행하니 실행이 됨...;;

**Fri Jul 10 2020**

- [x] 특정 아이디의 토큰으로 모든 사용자 정보를 변경할 수 있는 에러를 해결하기 위해..! 전체적인 복습의 필요성을 느낌. 프로젝트 처음부터 다시 만들기
- [x] javascript 100제 - 25번까지



**Thu Jul 09 2020**

- [x] `crypto-js` 와 `jsonwebtoken` 을 사용한 Backend API 제작 중 사용자 정보를 업데이트 하는 API에서 에러 발생. 특정 아이디가 발급받은 토큰으로 모든 사용자의 정보를 변경하는 문제 발생... 어디서 이런 문제가 발생한 건지 모르겠음
- [x] django 스터디 진행 - 사용자 app과 게시판 app 이 상호작용하는 프로젝트를 실습해보는 시간을 가짐. 자료의 순서가 얽혀있어서 그런지 sh님 작업 중 에러 발생..! config 폴더 setting의 `INSTALLED_APPS` 에서 App 등록 순서가 잘못된 것 같다고 dh가 말해줌..! 장고는 앱 등록 순서로도 에러를 뿜을 수 있다는 것을 알게 됨.. 

**Wed Jul 08 2020**

- [x] `jsonwebtoken`을 사용한 API 제작 중 토큰 값을 못 가져오는 문제가 생기는데 원인은 models의 users 모듈에서 index값을 받는 분기처리가 없었음..!
  - [x] if(options.idx) { `query += ' WHERE idx = ?';`  `value = *options**.*idx;` } 를 통해 index값만으로 사용자 정보를 불러와 비교하는 코드로 문제 해결



**Tue Jul 07 2020**

- [x] 자바스크립트 100제 푸는데 10번 별찍기를 제외하고는 13번까지 진행..! 별찍기 어렵다..
- [x]  `jsonwebtoken`을 사용한 API 제작 기법을 학습하는데..! 토큰 값을 못 가져 오는 문제가 생긴다...! 왜 값이 null로 나오는지 모르겠다..

**Mon Jul 06 2020**

- [x] 생활코딩 WEB2 Nodejs-MySQL
  - [x] 데이터를 입력 받는 부분에 sanitize-html 적용
- [x] 비사이드 인터뷰..!

**Sun Jul 05 2020**

- [x] django 게시판 만들어보기
- [x] 자바스크립트로 하는 자료구조와 알고리즘 chapter.1 보기

**Sat Jul 04 2020**

- [x] web2-nodejs-mysql 글쓰기 앱 학습 중 mysql 모듈 import 중 에러가 발생하여 mysql2를 대체 사용해 해결! 
- [x] velog에서 여러 글을 봄..! 취업 수기 등... 다시금 의지를 다잡자!
  - [x] [누가 이름을 함부로 짓는가 - 변수 네이밍]([https://velog.io/@mowinckel/%EB%88%84%EA%B0%80-%EC%9D%B4%EB%A6%84%EC%9D%84-%ED%95%A8%EB%B6%80%EB%A1%9C-%EC%A7%93%EB%8A%94%EA%B0%80](https://velog.io/@mowinckel/누가-이름을-함부로-짓는가))
  - [x] [아무도 가르쳐주지 않는 것]([https://velog.io/@mowinckel/%EC%95%84%EB%AC%B4%EB%8F%84-%EA%B0%80%EB%A5%B4%EC%B3%90-%EC%A3%BC%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%83](https://velog.io/@mowinckel/아무도-가르쳐-주지-않는-것))
  - [x] [신입 프론트엔드 개발자가 되기까지]([https://velog.io/@kimu2370/%EC%8B%A0%EC%9E%85-%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EA%B0%9C%EB%B0%9C%EC%9E%90%EA%B0%80-%EB%90%98%EA%B8%B0%EA%B9%8C%EC%A7%80](https://velog.io/@kimu2370/신입-프론트엔드-개발자가-되기까지))
  - [x] [해영인이 개발자로 전직한 이야기]([https://velog.io/@bong2030/%ED%95%B4%EC%98%81%EC%9D%B8%EC%9D%B4-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%A1%9C-%EC%A0%84%EC%A7%81%ED%95%9C-%EC%9D%B4%EC%95%BC%EA%B8%B0Wecode-%EB%B6%80%ED%8A%B8%EC%BA%A0%ED%94%84-%EC%88%98%EB%A3%8C%ED%9B%84%EA%B8%B0](https://velog.io/@bong2030/해영인이-개발자로-전직한-이야기Wecode-부트캠프-수료후기))

**Fri Jul 03 2020**

- [x] 생활코딩 web2-nodejs
- [ ] Javascript notion 문서 정리(findIndex, find, spread 등! 개념 점검)

**Thu Jul 02 2020**

- [x] react-native todo app 만듦. 복잡도가 높은 것 같고.. 아직 적응이 필요한 것 같다..!

**Wed Jul 01 2020**

- [x] 장고 게시판 왜 writer_id를 찾는 에러가 나는지 모르겠다. 이 이상은 django에 투자할 시간이 없을 것 같고, dh에게 에러를 찾아보도록 제안해봐야겠다.!
- [x] react-native 디버거를 같이 켜야 에러가 발생하지 않는다.. 사소한 건데..! 몰랐네
- [x] react-native 디버거를 작동시키지 못하는 에러가 발생할 경우 디폴트로 설정된 브라우저대신! 파이어 폭스를 써서 잠시 해결함.

**Tue Jun 30 2020**

- [x] react-native 세팅할 때 작성한 코드들은 src 안으로..!
- [ ] react-native.. 효율적으로 학습할 수 있는 방법이 없을까..
- [x] Counter App을 통해 Props와 State의 개념.. ! 학습
- [x] node.js jwt token 학습
  - [ ] jwt token 학습한 내용 핸드북에 정리하기

**Mon Jun 29 2020**

- [x] Django Study 진행.. polls앱 vote 페이지 에러가 난 것 같은데..! 교안 수정해야 함..!
- [x] ek님 블로그 만드는 것 도와드림
- [ ] eslint와 prettier 적용 과정에서 branch 꼬임..

**Sun Jun 28 2020**

- [x] hello world react-native
- [x] `react native no bundle url present` 서버를 실행시키지 않아서 만나게 된 에러..! `ios` 실행 이후 `npm start` !!

**Sat Jun 27 2020**

- [x] 이동욱님의 가이드를 따라 이력서 작성 
  - [x] 블로그나 gitbook을 통해 학습 내용을 정리하기
- [x] 김철수 지음의 <개발자의 글쓰기> 프롤로그와 문장과 단락을 구조화하는 법 독서

**Fri Jun 26 2020**

- [x] 교육센터에서 기업 면접 기회를 가짐
- [x] django study handbook에서 board 내용 분리하기 gitbook 수정

**Thu Jun 25 2020**

- [x] axios API를 모듈화해 사용할 때 `return memos.delete('/', memoId)` 인자에 이렇게 값을 전달하여 오류를 냄. `memos.delete(`/${memoId}`);` 백틱기호로 감싸서 전달해야 한다.
- [x] Memo application Refactoring 완료. vuex의 헬퍼 함수에 익숙해지면 우아한 코드를 작성하게 될 수 있을 것 같다.

**Wed Jun 24 2020**

- [x] 이력서 수정
- [x] 커피 한 잔 마시며 끝내는 VueJS 학습
  - [x] axios 이용하여 back-end API 연동

**Tue Jun 23 2020**

- [x] nodejs payment API 제작 어려움.. SQL Syntax 에러.. SQL에 대한 더 높은 이해가 필요함 - DML에 대한 학습과 숙련이 필요..!
- [x] aws s3를 이용하여 파일을 업로드 기능 학습
- [ ] protocol 학습 - 간단한 채팅앱 다시 만들기



**Mon Jun 22 2020**  

- [x] 커피 한 잔 마시며 끝내는 VueJS 학습
  - [x] 메모 관리 애플리케이션 만들기 localStorage app
- [x] django study 진행 - 첫 번째 hello world part
- [x] 블로그 logo 배경 흰색에서 투명으로 바꾸기
- [x] nodejs users CRUD API



**Sun Jun 21 2020**

- [x] 커피 한 잔 마시며 끝내는 VueJS 학습
  - [x] 메모 관리 애플리케이션 만들기
- [ ] view에서 css import를 간단하게 처리할 수도 있는데... 왜 어렵게 처리했지..?! 그냥 App.vue에서 import하면 된다



**Sat Jun 20 2020**

- [x] 커피 한 잔 마시며 끝내는 VueJS 학습
  - [x] Vuex
  - [x] Vue Router 
- [x] nodejs와 express를 이용한 put, delete API 제작

**Fri Jun 19 2020**

- [x] 블로그에 GA를 설정하고, django-study 포스트의 내용을 수정함
- [x] nodejs와 express를 이용해서 post와 get API 제작
- [x] productive-box가 정상적으로 작동하는 것 확인 

**Thu Jun 18 2020**

- [x] django study를 간단하게 진행함. sh님의 노트북에서 django를 설치할 수 없는 환경 설정 오류가 뿜어져 나옴. 아마 jupyter notebook과 anaconda와 같은 툴 때문이지 않을까 추측. 다음 회차에는 노트북을 바꿔 진행해보기로 함
- [x] 오늘은 블로그를 만들었고, 내일은 GA를 달자



**Wed Jun 17 2020**

- [x] `bitbar`로 커밋내역 메뉴바에서 확인할 수 있는 툴 작성
- [x] Django 스터디 준비하기(setting, polls, bookmark, board, login/logout/, todo-app)
  - [x] Django 스터디 자료 만들 준비 - gitbook 으로 배포
- [x] 깃허브 블로그 작업 진행
- [ ] 스토리북 UI도 써보자
- [ ] 1차 완성본 작업 이후 프로젝트의 깃허브 분리해보는 건 어떤가 
- [x] 공연 커뮤니티 사이트 배경색과 card item의 desc 항목 배경색 변경 



**Tue Jun 16 2020**

- [x] DB를 다시 공부하고, 전처리에 대해 학습하자
- [x] 키노트로 작성한 자료 녹화, 프로그램 시연 또한 간단 녹화하려고 했으나 핵심 키워드 분석 기능을 구현하지 못했음
- [x] 혼자 있으면 망한다. 결과물을 못 내서 망하는 게 아니라 다양한 상호작용 가운데 1+1이 3이 되는 기적을 경험할 수 있는 기회를 잃기 때문. "데이터 사이언티스트 혹은 데이터 아티스트는 팀이다" 라는 말이 공감됨 
- [x] `Protocol`과 `SocketIO` 학습. 내일 다시 복습하여 간단한 채팅앱 만들어 보기



**Mon Jun 15 2020**

- [x] 크롤링한 관람객 리뷰 데이터를 데이터베이스에 넣을 때 `try/catch` 를 통해 예외처리하여 넣으니 에러가 발생하더라도 데이터가 잘 들어간다. 자바스크립트는 싱글 스레드 언어임을 다시 한 번 기억하자!
- [x] 크롤링한 '공연중목록' 데이터도 데이터베이스에 넣으면 좋을 것 같다.
- [x] 커뮤니티 사이트 프로젝트 - Artist 항목에 대해 프론트와 백엔드 작업 진행
- [x] `vuewordcloud` 모듈 Test
- [ ] 최종 발표자료 프론트와 백엔드 부분 보충자료 작성하였고, 크롤링 부분 보충자료와 참고문헌 부분 작성해야 함
- [ ] 조성진 리뷰 데이터에서 가중치 구하기 => 실패 KoNLP 에러가 뜸
- [ ] 간단한 시연 영상도 만들 수 있다면 좋겠는데

**Sun Jun 14 2020**

- [x] 가령, 임주희 피아노 리사이틀 공연이 공연소개 이미지가 없다. 공연 소개 이미지가 없는 경우 포스터로 대체하는 코드를 작성하자. 삼항연산자를 사용해야 하면 될까? => 생각했지만 배열인 경우와 아닌 경우를 분기처리하여 아닌 경우 `[]` 을 감싸 배열로 만든 후에 `v-for` 디렉티브 문으로 데이터를 전달한다. 그럼 배열이든 아니든 다 출력이 가능하다.
- [x]  `v-if`  와 상응하는 `template v-else`를 사용하면 template 안에 `v-if="!isLoading"` 처럼 사용하는 중복을 피하자 즉, 같은 속성을 중복해서 `v-if`를 사용하지 말자..!
- [x] v-if와 v-show의 차이에 대해 다시 한 번 고민해보기. 화면을 다시 그려 에러를 줄일 수 있다면 당연히 `v-if`를 사용해야지
- [x] 공연 상세정보를 통해 조회한 공연 시설정보 기본키를 이용해서 시설 상세정보를 조회하는 Back-end API를 제작
- [ ] wordcloud도 만들어야 함
- [ ] 데이터를 조회할 때 한 번 조회했던 데이터는 저장하고, DB를 검색해 데이터가 없다면 쿼리 스크립트로 조회하는 API를 제작하자. 프로젝트 종료 이후에 만들기
- [ ] [swot 분석 => 자기소개서 작성하기전 swot분석 진행](https://app.lucidchart.com/documents#/templates?folder_id=) 

**Sat Jun 13 2020**

- [x] 검색창 적용하기 Test
- [x] Daum 지도..! 위치값을 인자로 넘기기만 하면 되지 않을까 생각했지만 SPA에서 구현하는데 어려움이 있음

**Fri Jun 12 2020**

- [x] 공연 상세페이지의 탭메뉴 UI 제작
- [x] 공연 상세 정보에 다음 맵을 구현 위해 테스트 코드 작성
- [x] 깃허브에 프로젝트 Repository 다시 정리하기

**Thu Jun 11 2020**

- [x] 최종 발표자료 피드백 받기 위한 준비

- [x] IT 서적 구매 예정 - 리액트를 조금씩은 해야 됨, js 알고리즘, vue 책!

- [ ] 특정 컴포넌트의 하위 컴포넌트에서 상위 컴포넌트의 데이터를 같이 건드리면 "상위 구성 요소를 다시 렌더링할 때마다 값을 덮어쓰므로 프로펠러를 직접 변경하지 마십시오." 라는 에러가 발생한다. 하위 컴포넌트로 데이터를 내려줄 때 아래 컴포넌트에서는 데이터를 건드리지 말자..!

  

**Wed Jun 10 2020**

- [x] 프로젝트를 진행할수록 전처리의 중요성에 더욱 깊게 이해하게 된다. 전처리는 단순히 데이터를 정리하는 일을 넘어서 중요한 데이터를 정리하고 테이블간의 관계를 만드는 일도 포함된다. 
- [x] 최종 발표 자료 작업
- [ ] 깃허브 프로필에 Daily 코딩 시작 적용하기 그리고 깃허브 블로그 새롭게 만들 준비



**Tue Jun 09 2020**

- [x] 판넬 초안 제작
- [x] Nodejs 학습한 폴더에 노출되면 안 되는 코드들이 있으므로 Repository 정리하기
- [x] Nodejs user API 학습

**Mon Jun 08 2020**

- [x] 삽질 List 😂

  - [x] 컴포넌트 등록 안 해놓고.. 다른 에러가 없는지 계속 고민함.. 
  - [x] v-else 태그 안 닫아서 에러... 어디서 났는지 계속 찾음..; v-else 태그를 안 닫으니 `v-else=''` 의 속성에 할당 연산자가 붙음..

- [x] Vue에서 제공하는 Computed 속성을 적극 활용하여 템플릿 안에 조건문 사용을 지양하자

- [x] 실습을 통해 만든 vue UI들을 프로젝트에 적용하기

  

**Sun Jun 07 2020**

- [x] Node.js 학습한 내용 handbook 저장소에 작성하고 gitbook으로 호스팅
- [ ]  Leetcode에서 Easy 문제 Two Sum을 풀려고 시도해봤는데, 어렵다..  가령, `nums = [3, 2, 3]`이고, `target = 6` 일때 `indexOf`  로 첫 번째 값의 인덱스를 조회하고, target과 첫 번째 인덱스의 값의 차로 두 번째 값을 찾은 뒤, 위치도 찾는 방법을 시도
  - [ ] 그렇지만 첫 번째 값과 두 번째 값이 같다면.. 인덱스를 찾는 게  아이디어가 안 떠올라서 막힘. 국내 사이트를 먼저 점령하고 해외로 넘어가야 하는 것인가 고민도 됨..!
- [ ] 탭메뉴, 검색창 UI 컴포넌트 작업 중..!

**Sat Jun 06 2020**

- [x] 학습한 내용을 정리하기 위해 gitbook 테스트..!
- [x] SQL 테이블 조작어 학습

**Fri Jun 05 2020**

- [x] 발표자료 aws 구조도에서 폰트와 이미지 크기 조정 그리고 자기소개서 수정
  - [ ] 꼼꼼한 발표자료를 위해 크롤러를 만들 때 어떤 사이트의 어떤 데이터를 가져왔는지..!도 기술해야 한다.
- [x] 검색창과 탭메뉴 UI 테스트 중..!

**Thu Jun 04 2020**

- [x] ~~6월 2일 고민했던 갱신되지 않는 정보 에 대해 실마리를 찾음. 내가 찾던 답이 음..! router.push()에 있는 것 같다고 추측~~
  - [x] `this.$router.push()` 를 사용하여 해결
- [ ] 새로고침하면 공연상세 페이지의 데이터가 다 날라가는데, 이를 해결할 수 있는 방법은 없을까 고민
- [ ] PPT를 두괄식으로.! 핵심 페르소나를 위해 만든 프로젝트를 먼저 공개하고, 이를 만드는 과정을 발표내용에 넣는다.
  - [ ] 포트폴리오에 참고자료 항목 기술하기

**Wed Jun 03 2020**

오늘은 학습에 시간을 쏟은 날

- [x] 검색창과 탭 메뉴를 구현하기 위해 학습 진행 중
- [x] 비동기 제어 디자인 패턴 맛보기 학습

**Tue Jun 02 2020**

- [x] 공연목록을 보여주는 페이지 제작
- [x] 공연상세 정보를 보여줄 수 있는 페이지를 제작하기 위해 데이터를 vuex에서 저장해놓았다가, 컴포넌트에서 state에 접근해서 가져간다음 url 요청하는 로직을 만듦.
  - [ ] 그렇지만 상세페이지에서 이전 정보가 불려오는 등 새로운 데이터로 갱신 되지 않는다.. 음.. 어떤 점 때문에 생긴 문제인지 찾는 중

**Mon Jun 01 2020**

- [ ] 공연 목록 정보 Database에 쌓기
  - 공연예정목록과 공연중목록은 잘 쌓이지만 공연완료목록이 쌓이지 않는다. 이게 무슨 경우일까 왜 _text가 없다고 나오는 건지.. 음.. null 값이 있거나 값이 없는 경우가 있는 것 같은데, 이럴 경우 sequelize에서 어떻게 처리해야 하는 것인지 아직 모르겠다.
- [x] 게시글, 댓글 모델 추가

**[⬆ back to top](#table-of-contents)**

---



**Sun May 31 2020**

이제까지 학습했던 내용을 복습 차원에서 정리해야겠다고 생각

- [x] Figma/README.md에 Figma프로젝트 세팅법과 명도 대비 차 맞추는 법 등 내용 추가
- [x] AppHeader를 url에 따라 다르게 표현하고 싶었지만 설계를 다시 해야 하나 싶을 정도.. 로 아이디어가 안 떠오름.. 프로젝트 종료 이후에 다시 생각해보기로 함

**Sun May 30 2020**

TIL과 기록의 중요성을 다시금 깨닫고, 나에게 맞는 방법을 시도!

- [x] 화면에 한 꺼번에 많은 데이터를 뿌리는 일을 피하기 위해 페이지네이션 기법을 선택. 블로그 포스팅을 보고 프로젝트에 적용하는 과정에서 computed 속성의 위력을 체험. computed를 통해 프론트에서 데이터를 들고 있다가 사용자와 상호작용할 수 있다 
- [ ] AppHeader를 URL 파리미터 값에 따라 다르게 표현하고 싶었지만 실패. 다른 방법으로 AppHeader에 라우팅 처리 시도 중



**[⬆ back to top](#table-of-contents)**