# Django



## Django 게시판 만들기 



### Base template

디자인의 기준이 되는 HTML 파일을 만들어서
다른 HTML 파일에서 기준이 되는 파일을 상속받고 화면을 구현하는 기법

헤드 태그내의 내용을 상속 받는다. 
이를 통해 
1. 중복을 제거
1. 유지보수가 용이


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Base</title>
    <!-- head 태그내에 Bootstrap 태그가 오면 된다. -->    
</head>
<body>
<!--  container  -->
<div class="container">
    {% block contents %}
    {% endblock %}

</div>
<!-- //container -->

</body>
</html>
```

