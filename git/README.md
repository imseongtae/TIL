# git

형상관리 프로그램인 git에 대해 숙지하고 있는 내용을 정리했습니다.

## Contents

  1. **[git init](#git-init)**
  1. **[기존 저장소 clone](#기존-저장소-clone)**
  1. **[status](#status)**
  1. **[add](#add)**
  1. **[commit](#commit)**


  1. **[gitignore](#gitignore)**


   

---

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

## status
현재의 상태를 확인하는 명령어

```
$ git status
```

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

## commit
파일이나 폴더의 추가, 변경 사항을 저장소에 기록하기 위한 모든 행동은 commit 명령에 의해 이루어진다.  
commit은 작업의 분기점이 되며, 변경사항을 비교하기 위한 기준이 된다.   
commit은 `git commit –m “commit log message”` 와 같이 작성한다.
commit 메시지는 어떠한 작업을 수행했는지 의미가 명확하게 전달되도록 작성한다 **git은 협업의 도구이므로!**  

```
$ git commit –m “initial commit”
$ git commit –m “git 폴더에 README.md 파일 추가”
```


### commit history
history log 확인을 통해서 저장소에서 어떠한 commit 들이 있었는지 확인할 수 있다. 
아래와 같은 명령어 조합을 통해서 최근의 commit message만 조회할 수 있다. 

```
$ git log --all --oneline --decorate --graph -10
```

### git을 능숙하게 다루려면 vi Editor 사용법에 대한 이해가 조금 필요하다!
위처럼 로그 메시지를 보는 명령어를 입력하면 :(콜론)을 출력한 상태에서 사용자 입력을 기다린다.  
커밋 히스토리는 무제한적으로 늘어날 수 있기 때문에 사용자의 입력을 통해서 중단할지 아니면 계속해서 보여줄지를 결정해야 하는데, `q` 를 누르면 git log 명령은 중지된다. 



## gitignore

`.gitignore` 파일을 생성하여  
관리하지 않을 파일 및 폴더를 설정할 수 있다.   
주의할 점은 add 가 한 번 수행된 파일은 `.gitignore` 파일에 의해 ignore 되지 않는다.
