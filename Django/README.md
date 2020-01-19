# Django


Django를 학습한 내용을 문서화합니다. 


## Table of Contents

  1. [Polls](./Polls.md)
  1. [Bookmark](./Bookmark.md)
  1. [User](./User.md)
  1. [Board](./Board.md)
  
  
---


## Setting

### config setting

`config` 뒤에 `.`을 찍지 않으면 config 폴더 아래에 config 폴더가 생기므로  `config .`로 프로젝트를 생성할 수 있도록 주의한다

```
django-admin startproject config  # X
django-admin startproject config . # O
```

### Django server 실행

프로젝트가 서버가 올바르게 생성되었는지 확인하기 위하여!


### ALLOWED_HOSTS
`DEBUG`가 `True`이면 개발 모드 `DEBUG`가 `False`이면 운영모드로 장고가 인식하므로  
운영모드로 설정할 경우에는 서버의 IP나 도메인을 지정해야 한다.  
개발모드는 값을 따로 설정하지 않아도 `['localhost']`로 인식함

```python
DEBUG = True
ALLOWED_HOSTS = []
```

### INSTALLED_APPS
장고에서는 `INSTALLED_APPS`에 애플리케이션이 등록되어야 하는데, 이 때 간단하게 애플리케이션의 이름만 지정할 수 있지만, 더 정확하게는 설정 클래스로 등록해야 한다. 설정 클래스는 'polls' 앱의 `apps.py`에 생성된 클래스 'PollsConfig'를 말한다.

```python3
INSTALLED_APPS = [
  ...
  'polls.apps.PollsConfig',
]
```

### DATABASES Engine

```python
DATABASES = {
  'default': {
    'ENGINE': 'django.db.backends.sqlite3',
    'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
  }
}
```


### TIME_ZONE
`UTC` 세계 표준시를 한국시간으로 변경

```python
TIME_ZONE = 'Asia/Seoul'
```


### SQLitebrowser
**Homebrew**  
If you prefer using Homebrew for macOS, our latest release can be installed via Homebrew Cask:

```
brew cask install db-browser-for-sqlite
```
