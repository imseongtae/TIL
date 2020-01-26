# git

형상관리 프로그램인 git에 대해 숙지하고 있는 내용을 정리했습니다.

## git이란?

Version Control System(VCS) 중 하나이다.  
파일을 저장하는 서버가 있는 것은 동일하지만 수정을 위해 프로젝트 전체를 로컬에 다운 받은 뒤 수정하는 분산 VCS 이다.

![예시 이미지](https://w.namu.la/s/a0c8ce6352cbc4b4275719c6d3fff1eb6f501d9a7a2d8c78771f5c4e3a3de7f4386e9b9231704978b7bb0b9c9b640f44e8760f82f6e65c2401c42afad7cc355b3d434623d8fab2d60b128e7fe4e3b0d8414d354799765a321642c3db3693bd34)

## Contents

  1. **[git version](#git-version)**
  1. **[git config](#git-config)**
  1. **[git init](#git-init)**
  1. **[기존 저장소 clone](#기존-저장소-clone)**
  1. **[가장 중요한 명령어](#가장-중요한-명령어)**
  1. **[status](#status)**
  1. **[add](#add)**
  1. **[commit](#commit)**
  1. **[push](#push)**
  1. **[pull](#pull)**
  1. **[branch](#branch)**
  1. **[reset](#reset)**
  1. **[revert](#revert)**
  1. **[merge](#merge)**
  1. **[rebase](#rebase)**
  1. **[gitignore](#gitignore)**
  1. **[vi Editor](#vi-Editor)**

   
---

## git version
git의 현재 버전과 설치 유무를 확인할 수 있다.

```
$ git --version
```

## git config

환경설정을 확인할 수 있음

```
$ git config --list
```

### configure user and email
`user.name`과 `user.email`을 설정하지 않으면 commit 을 하여도 잔디밭이 가꾸어지지 않는다..!

```
$ git config --global user.name 아이디
$ git config --global user.email 이메일 주소
```

**[⬆ back to top](#contents)**

## git init
`git init` 명령을 실핼하면 git은 `.git` 이라는 하위 디렉토리를 만들고, .git 디렉토리에는 저장소에 필요한 뼈대 파일이 생성된다. 그리고 본격적으로 파일 관리 및 추적을 시작할 수 있게 된다.

```
$ git init
```


## 기존 저장소 clone

```
$ git clone <remote-url>
```

### 원격 저장소의 url을 변경하고 싶을 때

```
$ git remote set-url origin <remote-url>
```

## 가장 중요한 명령어
`git`은 협업을 위한 도구이므로 작업을 시작하기 전에 **항상 협업을 위한 준비**를 해야 한다. 이를 위해서  
아래의 명령어를 통해 원격 저장소의 작업 내용을 로컬 저장소로 반영하고, 나의 `branch`가 `master`인지 내가 생성한 `branch`인지 확인해야 한다. 

```bash
$ git pull origin master
$ git branch
```

## status
현재의 상태를 확인하는 명령어

```
$ git status
```

**[⬆ back to top](#contents)**


## add
다음 commit에 추가하기 위해 파일을 staged 상태로 만듦
add 명령은 아래처럼 전체를 보낼 수도 있고

```
$ git add –A
$ git add ––all
$ git add .
```

특정 파일만 staged 상태로 만들 수도 있다.
`$ git add <path/file-name>` 경로와 파일명 설정

```
$ git add README.md
```

**[⬆ back to top](#contents)**

## commit
파일이나 폴더의 추가, 변경 사항을 저장소에 기록하기 위한 모든 행동은 commit 명령에 의해 이루어진다.  
commit은 작업의 분기점이 되며, 변경사항을 비교하기 위한 기준이 된다.   
commit은 `git commit –m “commit log message”` 와 같이 작성한다.
commit 메시지는 어떠한 작업을 수행했는지 의미가 명확하게 전달되도록 작성한다 **git은 협업의 도구이므로!**  

```
$ git commit –m “initial commit”
$ git commit –m “git 폴더에 README.md 파일 추가”
```

> 미래의 나를 위해서 커밋 메시지를 잘 작성하자. 

### add commit

git에 의해 추적(`tracked`)되는 파일은  
`git commit -am "commit log message"` 를 통해서 `add`와 `commit`을 한 번에 수행할 수 있다. 
> 다만, `untracked` 파일은 `add`와 `commit` 한 번에 할 수 없음 
```
$ git commit –am “README.md 문서에 git에 대한 내용을 update”
```

### commit history
history log 확인을 통해서 저장소에서 어떠한 commit 들이 있었는지 확인할 수 있다. 
아래와 같은 명령어 조합을 통해서 최근의 commit message만 조회할 수 있다. 

```bash
$ git log --all --oneline --decorate --graph -10
```
### git shortlog 
간단하게 commit message를 확인해볼 수 있는 명령어도 있다.

```bash
$ git shortlog
```

### git diff 
`git diff`를 통해서 어떤 부분이 변경되었는지 확인할 수 있다.

**[⬆ back to top](#contents)**


## push
로컬 저장소에서 `commit`한 변경 사항을 `push`하면 원격저장소에 반영되는데,  
`git push origin <branch-name>`과 같이 명령어를 입력한다.  
`-u`를 붙이면 원격 저장소에 로그인하는 번거로움을 줄일 수 있다.

```
$ git push origin master
$ git push -u origin master
```

## pull
원격저장소에 있는 데이터를 로컬저장소로 가져와서 반영함.  
`pull`은 `fetch` 명령을 실행하고 자동으로 `merge`를 실행하는 원리를 가지고 있음

**중요! 작업하기 전에 항상 git pull을 통해 원격 저장소의 작업을 당겨와야 한다.**

```
$ git pull
$ git pull origin master
```
**[⬆ back to top](#contents)**

## branch

`branch`는 개발의 진행 흐름을 나타낸다.   
새로운 브랜치는 주로 새로운 기능을 개발할 때 생성하며 나중에 master 브랜치와 합치는 용도로 사용한다.
배포 완료된 브랜치만 master 브랜치에 `merge`해서 안정 버전의 코드만 master 브랜치로 두자.

브랜치는 `git branch <branch-name>` 명령어를 통해 생성할 수 있다. 

### 브랜치 보기

```bash
$ git branch
```

### 생성하기

```bash
$ git branch <branch-name>
```

### 브랜치 이동

```bash
$ git checkout <branch-name>
```

### 브랜치 삭제

```bash
$ git branch -d <branch-name>
```


**[⬆ back to top](#contents)**


## reset
### reset은 과거로 되돌아가기 위해 사용, 혼자 로컬에서 작업할 때 유용하다.
현재 커밋 시점이 HEAD이고, 여기서 한 칸 뒤로 되돌리고 싶을 때 reset을 사용한다.

```bash
$ git reset HEAD~1
```
### reset 주의사항
`reset`을 실행하면 내가 실수한 커밋의 내용과 기록 자체가 사라진다.  
이로 인해 당황할 수 있는데, 이를 해결하기 위해서는 깃허브에 실수했던 걸 push해놓고 리셋하는 게 좋다.

`git reflog`라고 `reset`을 되돌리는 방법이 있긴하지만 이건 가급적 쓰면 안된다.
애초에 안 쓰는 게 가장 좋으므로!

### reset의 3가지 모드
`reset`을 통해 어느 단계로 돌아갈지 선택할 수 있다.
되돌리는 시점에 따라서 `soft`, `mixed`, `hard`로 구분되며,  
`mixed`가 기본이다. `hard`를 하면 변경내역이 다 사라지므로 안 하는 게 좋다.   
`mixed`가 기본인 건 이유가 있는 법!

| 파일 상태에 따른 `reset`모드 |  
|:---:|
| **new commit** |
| add한 내용, Staged -> soft | 
| 수정한 내용, Modified -> mixed |
| **기존 commit**, Unmodified -> hard |


### git reset --hard
`git reset --hard` 명령을 입력하면 기존 파일로 되돌아간다.
수정한 내용(Modified)과 add한 내용(Staged)에서 기존 커밋으로 되돌아간다.
**커밋 이전에만 쓸 수 있고, 혼자 작업할 때만 사용하기 유용한 명령이다..!**

```bash
$ git reset --hard
```
**[⬆ back to top](#contents)**


## revert 
### revert는 과거 실수를 바로잡기 위해 사용, 협업할 때 사용해야 한다.
`revert`는 실수를 인정하고 새로운 커밋을 통해 실수 이전의 지점으로 돌리는 명령어이다.  
> 깃헙(원격 저장소)에 올라간 것은 못 바꾼다고 생각하는 게 좋다. 괜히 이것을 고치려다가 큰 실수를 할 수도 있다. 

```bash
$ git revert HEAD
```

위의 명령어를 입력하면 vim에디터가 나오는데! 상단에 커밋 메시지를 적고,  
`:wq`를 통해 에디터를 종료하면 된다.

`revert`는 과거 실수를 바로 잡고, 되돌리지만 이 과정을 `commit`으로 남긴다.
실수한 내용이 그대로 남지만 **협업**할 때 주로 사용한다.
가령, 원격 서버에 `push`까지 했을 경우 내 실수를 만회하기 위해 `reset`을 해봤자  
다른 팀원들은 `reset`을 적용받지 못한 채 작업을 이어나가는 문제가 발생할 수 있다.  
그러므로 실수가 발생했더라도 `revert`를 통해서 실수를 만회(실수를 만들어내기 이전 지점으로 돌아가는)하는 커밋을 퍼뜨리고 이러한 변경사항을 공유해야 한다. (이를 통해 동료에게 실수를 만회한 작업사항을 같이 적용할 수 있다.) 

### commit 아이디만 있으면 과거의 어느 지점으로도 revert할 수 있다.

**[⬆ back to top](#contents)**

## merge

master 브랜치를 제외한 모든 브랜치는 부모 브랜치가 있다. 브랜치로부터 파생된 브랜치는 상황에 따라 버려질 수도 있지만 대부분 다른 브랜치와 합쳐져 **자신이 가지고 있던 의미와 목적을 다른 브랜치에 전달**한다. 이것을 병합(merge)이라고 한다.

`merge`가 반영될 브랜치로 `checkout`하여 이동 후,  
`git merge <branch-name>`명령을 이용해서 병합하기

```bash
$ git merge mac
```

### Conflict가 발생한 경우
서로 다른 브랜치에서 같은 줄을 수정했을 경우, 충돌이 발생한다.
아래처럼 충돌 내용을 수정해야 하는 상황이 생기는데,  
꼭 둘 중 하나만 골라야 하는 것이 아니라 하나만 합쳐지기만 하면 된다.

> `conflict`가 발생하면 프로그래머간에 소통을 통해서 코드를 고쳐야 한다. 임의로 코드를 바꾸면 문제가 생길 수 있으므로 주의해야 한다.

```
<<<< HEAD

====

>>>> mac
```

### abort, merge를 해제하기
`merge`한 것을 끊을 수 있다.

```bash
$ git merge --abort
```

### 코드를 수정하여 add, commit을 하면 변경사항이 반영되어 merge가 이루어짐


## rebase
`rebase`는 `merge`와 같은 역할을 하지만 commit 그래프를 한 줄로 만들 수 있다

### merge와 rebase 중 더 편한 것을 사용하면 된다.
`merge` 와 마찬가지로 master 브랜치에서 병합할 브랜치를 목적어로 둔 명령어를 입력한다.

```bash
$ git rebase mac
```

### rebase abort, rebase를 해제하기
`rebase`도 `merge`와 마찬가지로 `--abort`로 연결을 해제할 수 있다.
해제하면 `rebase`나 `merge` 이전 시점으로 돌아간다.

```bash
$ git rebase --abort
```

### rebase continue
병합할 브랜치가 master 브랜치의 밑으로 들어가서 
커밋 그래프가 한 줄로 쭉 잉어지도록 하는 명령어이다. 

```bash
$ git rebase --continue
```


**[⬆ back to top](#contents)**


---

## gitignore

`.gitignore` 파일을 생성하여  
관리하지 않을 파일 및 폴더를 설정할 수 있다.   
주의할 점은 `add`가 한 번 수행된 파일은 `.gitignore`에 의해 ignore되지 않는다.

**[⬆ back to top](#contents)**

## vi Editor 
### git을 능숙하게 다루려면 vi Editor 사용법에 대한 이해가 조금 필요하다!
`git shortlog`처럼 로그 메시지를 보는 명령어를 입력하면 :(콜론)을 출력한 상태에서 사용자 입력을 기다린다.  
커밋 히스토리는 무제한적으로 늘어날 수 있기 때문에 사용자의 입력을 통해서 중단할지 아니면 계속해서 보여줄지를 결정해야 하는데, `q` 를 누르면 git log 명령은 중지된다. 

| 명령어 | 설명 | 
|---|---|
| `vi <filename>` | 파일의 편집 | 
| `i` | 데이터 입력 | 
| `esc` | 작성이 다되면 esc키를 누른다 | 
| `:wq` | esc 이후 `:`을 누른후 write quit, 파일을 빠져나감  | 
| `q!` | 강제로 파일을 나올때 |
| `cat` | 파일의 내용 확인 |
| `--help` | 세부 옵션 확인 |

**[⬆ back to top](#contents)**

## git 프롬프트 한글로 변경하는 법

윈도우의 경우 git bash는 한글로 나오는데 명령 프롬프트가 한글이 안 될 경우, 
한글로 바꾸고 싶을 때 명령 프롬프트의 언어 설정을 변경한다.
프롬프트나 터미널 별로 한글 설정하는 방법이 다를 수 있다.

### for Windows
```bash
$ set LC_ALL=ko_KR.UTF-8
```




### 깃으로 만나는 모든 에러는 구글을 통해 해결할 수 있다. 


