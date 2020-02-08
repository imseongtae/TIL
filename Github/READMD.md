# Github :octocat:

깃허브가 강력한 협업 도구라는 사실을 새롭게 깨닫습니다. 

그 내용을 정리합니다.

## What is the Github?

그저 GUI 기반의 형상관리 서비스라고 생각했었지만..! 

이번 기회에 많은 것을 느끼고 생각하게 되었습니다. 스스로가 깃허브에 대해 어떠한 태도를 갖는지도 중요한 지점인 것 같습니다.

깃허브를 잘 관리하면 성장에 도움이 될 거라는 확신이 들었습니다.



## Table of Contents

1. [Types](#types)

1. [Collaborator 추가](#Collaborator-추가)

1. [참고 문헌](#참고-문헌)

   

---



## 개발 워크플로우 만들기

### 커밋에 이슈 번호를 다는 이유

커밋에 이슈 번호를 붙이면 **이슈 기반 버전관리**를 할 수 있다. 

> git hook을 쓰면 이슈번호를 자동으로 달 수 있지만.. 이건 아직은 깊은 개념 같다.. 조금 더 지난 다음에..! 키워드로..! 남겨두어야 할 영역

**이슈 기반 버전관리**는 프로젝트를 '이슈 작성' -> '개발' -> '이슈 해결'의 흐름으로 만들 수 있는데, 이렇게 하면 개발자의 작업 목적이 명확해지고, 프로젝트의 진척 상황을 손쉽게 관리할 수 있다. 

### work-flow

1. 새로운 issue를 열고, 번호 확인
2. 로컬 저장소에 새로운 브랜치 생성. "issue 번호-설명" 
3. issue에 적어둔 작업 완료
4. 작업을 테스트하고 완료되면
5. 수정사항을 커밋하고 푸시한다. github가 커밋을 추적할 수 있도록 커밋 메시지 안에 이슈 번호를 적는다.
6. 작업이 완료된 브랜치를 메인 브랜치에 merge한다.
7. 이슈의 내용이 완료되면 issue를 닫는다.

### 1. New  issue or Convert to issue

이슈를 생성하고, 라벨, **Assignees**, **Labels**, **Projects** 등을 설정

### 2. 로컬 저장소에 작업 브랜치 생성

```bash
git checkout -b 4-Github 
git push --set-upstream origin 4-Github # 로컬브랜치와 원격 브랜치 연결
```

### 3. issue에 적어둔 작업을 완료

완료단계에서는 작업을 열심히 완료하면 됨!

### 4. 작업 테스트!

내가 읽은 블로그 포스트에서는 이 단계에서 lint 체크를 하지만..  아직 나에게는 먼 영역..

### 5. 커밋과 푸시

```bash
git status
git add .
git commit # 커밋 header와 body는 따로 작성
```

```bash
[#4] Github (작업 message) # 커밋 메시지 제목과 본문에 이슈 번호 입력

---
commit body
---

Resolves #4
```

```bash
git push
```

### 완료된 작업을 Main branch에 병합

```bash
git rebase master
git checkout master
git pull --rebase=preserve
git merge 4-Github
```

### close issue

이제는 이슈와 브랜치를 정리한다. 먼저 issue에 가서 `Closed`를 한다.

그리고 프로젝트의 칸반보드에서 `Done` 항목으로 넘어간 걸 확인한다

```bash
git push origin -d 4-Github && git branch -d 4-Github
```

**Insights**의 `Network graph`를 확인하여 일렬로 정렬된 것을 확인한다.!





## Collaborator 추가

### Contributor , 기여자

`Contributor`는 프로젝트 관리자는 아니지만, 프로젝트의 커밋에 기여하는 사람을 일컫는다.

`push` 권한은 `프로젝트 관리자와 Collaborator`만이 가지고 있으므로, 프로젝트에 기여하고 싶은 사람은  `Fork`하여 `push`를 진행하면 원래의 프로젝트로 내용을 보낼 수 있다. 이를 `Pull Request`를 생성한다고 말한다.

`Pull Request`가 생성되면 토론을 거쳐 계속해서 `commit`을 진행하고 프로젝트 관리자는 `Pull Request`를 검토해 **merge하거나 reject**하며 마무리 짓는다. 이때 `Pull Request`가 받아들여지면 이 사람은  `Contributor`가 된다.

### Collaborator, 협력자

**Collaborator**는 `push`, `pull` 권한을 모두 가지고 있는 프로젝트의 공동 책임자를 뜻한다.

`Pull Request`를 통해 누구나 `Contributor`가 될 수 있는 것과는 상반되게,   `Collaborator`는 프로젝트 관리자가 직접 추가해줘야 권한을 얻는다. 하나의 프로젝트를 중점적으로 개발하는 개발자들은 `Collaborator`로 등록하여 작업하는 것이 효율적이다.

### Collaborator 추가하는 방법

[Collaborator 추가하기](https://hyoje420.tistory.com/41)









## 참고 문헌

- [github 하나로 1인 개발 워크플로우 완성하기: 이론 편](https://www.huskyhoochu.com/issue-based-version-control-101)
- [github 하나로 1인 개발 워크플로우 완성하기: 실전 편](https://www.huskyhoochu.com/issue-based-version-control-201)
- [깃허브(GitHub)로 취업하기](https://sujinlee.me/professional-github/)
- [Collaborator 추가하기](https://hyoje420.tistory.com/41)
- 

