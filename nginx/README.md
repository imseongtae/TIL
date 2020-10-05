# nginx


## nginx install

```bash
sudo apt-get install nginx
```

## nginx confing 

```bash
cat /etc/nginx/nginx.conf
vim /etc/nginx/nginx.conf
```


## certbot-auto를 위한 nginx conf setting

certbot-auto를 실행하기 전
아래처럼 설정해놓고 `./certbot-auto`를 실행

```bash
server {
        server_name chassie.me;
        listen 80;
        location / {
                proxy_set_header Host $host;
                proxy_pass http://127.0.0.1:8080;
                proxy_redirect off;

        }
}
```

