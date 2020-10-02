# ubuntu




## ubuntu에 Nodejs 설치

### ubuntu 초기 설정 명령어

```bash
$ sudo su 
$ sudo apt-get update
$ sudo apt-get install -y build-essential
$ sudo apt-get install curl
$ curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash --
$ sudo apt-get install -y nodejs
```

### 명령어 실행의 의미
1. `sudo su`를 통해 루트로 이동. 경로에 대한 복잡도를 낮추기 위해
1. 우분투 업데이트
1. Node에서 필요로 하는 것들 설치
1. ubuntu에 curl은 기본 설치되어 있음
1. Node.js 설치 파일 다운로드
1. Node.js 설치파일을 실행하여 Node.js 설치


