# Django



## Django 게시판 만들기 


### Base template: MVT의 T를 확장하여 상속하기

디자인의 기준이 되는 HTML 파일을 만들어서
다른 HTML 파일에서 기준이 되는 파일을 상속받고 화면을 구현하는 기법

헤드 태그내의 내용을 상속 받는다. 
이를 통해 
1. 중복을 제거
1. 유지보수가 용이

#### 상속하는 방법

1. children 파일에서 구현할 영역을 `{% block contents %}`와 `{% endblock %}`를 통해 설정

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

#### 상속받는 방법

1. `{% extends 'base.html' %}` 최상단에 작성
1. 시작 태그처럼 사용 `{% block contents %}`
1. 구현할 화면의 템플릿을 만들고
1. 닫는 태그처럼 사용 `{% endblock %}`

```html
{% extends 'base.html' %}

{% block contents %}
<!--  Login  -->
<div class="row mt-5">
    <div class="col-12 text-center">
        <h1>로그인</h1>
    </div>
</div>

<div class="row mt-5">
    <div class="col-12">
        <form method="post" action=".">
          <div class="form-group">
            <label for="username">사용자 이름</label>
            <input type="text" class="form-control" id="username" name="username" placeholder="사용자 이름">
          </div>
          <button type="submit" class="btn btn-primary">로그인</button>
        </form>
    </div>
</div>
<!--  //Login  -->
{% endblock %}
```




