# Renew certbot-auto(SSL)
SSL 인증서를 프로그래머가 갱신하는 대신 cron을 통해 자동화할 수 있다.
이를 위해 이해해야 하고 있어야 할 지식👇

```txt
/etc/crontab, /etc/cron.d 등은 시스템이 관리하며,
crontab -e -l 등 명령어를 통한 설정은 개별 유저 crontab 입니다.
즉 서비스는 같은 서비스이고 하나로 움직이나 별개로 관리가 됩니다..
```

> 시스템 crontab에 certbot-auto 를 자동화하는 명령을 등록해야 함

## table of contents
- [설치](#설치)
- [자동 갱신](#자동-갱신)
- 시스템 crontab에 등록할 명령어
- [Troubleshooting](#troubleshooting)
- [certbot-auto 명령어](#certbot-auto-명령어)
- [Reference](#reference)


## 설치
nginx에 프록시에 대한 초기 설정이 이루어진 후

```bash
wget https://dl.eff.org/certbot-auto

# 실행권한 추가
chmod a+x certbot-auto

# 실행
/certbot-auto
```

### snap과 nginx
snap과 nginx를 통해서 letsencrypt를 설치할 수도 있음  
> 이 방법잉 더 쉬울 수도 있음 

```bash
sudo snap install certbot --classic
sudo apt-get install nginx

#
sudo certbot --nginx
```


## 자동 갱신

### 크론탭이 작성될 위치
[관리자 권한으로 크론탭을 작성할 경우, 크론탭이 작성될 위치](https://ponyozzang.tistory.com/401) 를 참고한다..!

> 관리자인 root 권한으로 프로그램을 실행해야 하는 경우에는 /etc/crontab에 작성을 해야 합니다. 또는 /etc/cron.d 안에 crontab 파일에 설정을 해도 자동으로 실행됩니다. 시간 단위, 분 단위, 일 단위, 월 단위 등 정기적으로 실행할 파일들의 설정을 할 수 있도록 나눠져 있습니다. 

```bash
/etc/crontab
/etc/cron.d
/etc/cron.daily/
/etc/cron.weekly/
/etc/cron.hourly/
/etc/cron.monthly/
```


## 시스템 crontab에 등록할 명령어
제로초님 블로그 및 다른 블로그 글을 참고해 작성한 코드
관리자 권한을 가진 매일 실행할 크론탭을 `/etc/cron.d/certbot` 의 경로에 등록한다.

### 등록할 명령어 타입1

```bash
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
0 */12 * * * root certbot-auto -q renew --nginx --renew-hook 'service nginx reload'
```

### Test


```bash
# renew certbot-auto 
0 */12 * * * /usr/local/bin/certbot-auto -q renew --nginx --renew-hook 'service nginx reload'

# renew certbot-auto 
0 */12 * * * /home/ubuntu/certbot-auto -q renew --nginx --renew-hook 'service nginx reload'

# Test를 위해 한 시간마다 인증서 갱신
# renew certbot-auto 
0 */1 * * * /home/ubuntu/certbot-auto -q renew --nginx --renew-hook 'service nginx reload'
```




## Troubleshooting
갱신을 위해 아래 명령을 실행하면 

```bash
./certbot-auto renew 
```
아래와 같은 에러를 만나게 되고, 이를 해결하기 위한 방법을 연결된 링크를 통해 확인하라고 함

```bash
./certbot-auto has insecure permissions!
To learn how to fix them, visit https://community.letsencrypt.org/t/certbot-auto-deployment-best-practices/91979/
```

해당 문서에서는 `certbot-auto` 경로를 `/usr/local/bin/`로 바꾸라고 함  
> 이를 고려해볼 때, `certbot-auto`를 처음부터 해당 경로에 설치하는 게 좋을 것 같다.

### 경로 변경

```bash
sudo mv certbot-auto /usr/local/bin/
```



## certbot-auto 명령어

```bash
# renew 작동 확인 명령어
./certbot-auto renew --dry-run

# certbot-auto 갱신, 갱신을 위해선 --dry-run 을 제거
./certbot-auto renew
./certbot-auto -q renew 
./certbot-auto renew --quiet --no-self-upgrade

# 인증서 관련 정보 확인
./certbot-auto certificates
```



## Reference
- [Let's Encrypt SSL 인증서 자동 갱신 설정 방법](https://devlog.jwgo.kr/2019/04/16/how-to-lets-encrypt-ssl-renew/)
- [certbot-auto has insecure permissions! 오류](https://sang12.co.kr/219/certbot-auto-has-insecure-permissions%21-%EC%98%A4%EB%A5%98)
- [관리자 권한으로 크론탭을 작성할 경우, 크론탭이 작성될 위치](https://ponyozzang.tistory.com/401)
