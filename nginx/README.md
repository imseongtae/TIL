# nginx


## table of contents
1. [nginx install](#nginx-install)
1. [nginx confing](#nginx-confing)
1. [nginx.conf setting for certbot-auto](#nginx.conf-setting-for-certbot-auto)


---

## nginx install

```bash
sudo apt-get install nginx
```

## nginx confing

```bash
cat /etc/nginx/nginx.conf
vim /etc/nginx/nginx.conf
```


## nginx.conf setting for certbot-auto
`certbot-auto`를 통해 인증서 발급을 실행하기 전에 설정할 `nginx.conf` 내용

certbot-auto를 실행하기 전
아래처럼 설정해놓고 `./certbot-auto`를 실행

```bash
server {
        server_name example.com;
        listen 80;
        location / {
                proxy_set_header Host $host;
                proxy_pass http://127.0.0.1:8080;
                proxy_redirect off;

        }
}
```


## https인 경우 www를 non-www 주소로 리다이렉트

- 기존 작성되어 있던 초기 리다이렉트 코드

```bash
server {
  if ($host = example.com) {
      return 301 https://$host$request_uri;
  }
  # managed by Certbot
  server_name example.com;
  listen 80;
  return 404; # managed by Certbot
}
```

- 기존 작성되어 있던 내용을 아래처럼 변경
- 80포트 http 요청을 443 https 요청으로 리다이렉트

```bash
server {
  listen 80;
  server_name example.com www.example.com
  return 301 https://chassie.me$request_uri;
}
```

- https www 요청을 non-www 로 리다이렉트하는 설정 

```bash
server {
    listen 443 ssl;
    server_name www.example.com;

    location / {
        return 301 https://example.com$request_uri;
        expires epoch;
    }
    # SSL 인증서 설정은 non--www와 동일하게 해야 함
    # 이곳에서는 사이트 경로 설정이나 XE 설정, PHP 연동 설정 등을 하지 않음
}
```



## 참고문헌

- [nginx에서 https, www 리다이렉트 처리하는 법](https://xetown.com/tips/1172256)
- [Www에서 Non-Www 도메인으로 설정방법, Nginx](https://webisfree.com/2018-03-30/www%EC%97%90%EC%84%9C-non-www-%EB%8F%84%EB%A9%94%EC%9D%B8%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%EB%B0%A9%EB%B2%95-nginx)