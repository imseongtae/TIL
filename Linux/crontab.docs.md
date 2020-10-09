# crontab


## table of contents
- [crontab](#crontab)
- [주기별 예제](#주기별-예제)
- [Reference](#reference)

---


## crontab
crontab을 사용하기 위해선 어느 사용자에서 사용할 것인지 미리 정하고 진행해야 한다. 

크론탭을 활용하기 위해선 아래 내용을 이해해야 함

```
/etc/crontab 은 시스템이 관리하는거고
crontab -e -l 등은 개별 유저 crontab 입니다.
즉 서비스는 같은 서비스이고 하나로 움직이나 별개로 관리가 됩니다..
```

- **root에 등록할 경우는 시스템 crontab에 등록해야 한다.**
- 사용자에서 crontab을 설정할 경우, sudo su로 실행하면 안 되고 user에서 실행해야 함
- sudo su에서는 크론탭 편집기가 올바르게 작동 안 함, 그 이유는 일반 사용자만 크론탭 편집기를 사용할 수 있음
- 사용자를 전환할 수 있음. `sudo su` 로 넘어갔을 경우 `su ubuntu` 로 다시 넘어오기
- `crontab`에 `sudo`를 붙이느냐 아니냐에 따라서 차이가 크다.
- 근데 시스템에 등록하는 경우 또 다를 수 있다.

### 명령어

```bash
# Crontab 보기 /  현재 크론탭에 어떤 내용이 들어있는지 보기
$ crontab -l

# Crontab 편집 /  크론탭 설정 찾으로 이동하여 각종 크론탭 명령어를 입력후 콜론(:) 입력 후에 wq 를 입력해 크론탭을 갱신
$ crontab -e

# Crontab 실행 로그
$ view /var/log/syslog

# Crontab 삭제
$ crontab -r
```

## 주기별 예제

```bash
# 매분 test.sh 실행
* * * * * /home/script/test.sh

# 매주 금요일 오전 5시 45분에 test.sh 를 실행
45 5 * * 5 /home/script/test.sh

# 매일 매시간 0분, 20분, 40분에 test.sh 를 실행
0,20,40 * * * * /home/script/test.sh

# 매일 1시 0분부터 30분까지 매분 tesh.sh 를 실행
0-30 1 * * * /home/script/test.sh

# 매 10분마다 test.sh 를 실행
*/10 * * * * /home/script/test.sh
```

### 복잡한 실행

```bash
# 5일에서 6일까지 2시,3시,4시에 매 10분마다 test.sh 를 실행
*/10 2,3,4 5-6 * * /home/script/test.sh
```



## Reference
크론탭을 상세하게 알려주는 블로그
- [리눅스 크론탭(Linux Crontab) 사용법](https://jdm.kr/blog/2)

- [관리자 권한으로 크론탭을 작성할 경우, 크론탭이 작성될 위치](https://ponyozzang.tistory.com/401)
- [시스템 크론탭과 개별 유저 크론탭의 차이](https://www.phpschool.com/gnuboard4/bbs/board.php?bo_table=qna_install&wr_id=65273)
