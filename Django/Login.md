# Login/Logout

## Table of Contents

  1. [BaseTemplate](#BaseTemplate)
  1. [Login](#Login)
  1. [References](#references)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Destructuring](#destructuring)

---


### BaseTemplate
#### MVT의 T를 확장하여 상속하기

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
<!--  block과 endblock 사이에 내용을 작성해주면 된다.  -->
<div class="row mt-5">
    <div class="col-12 text-center">
        <h1>로그인</h1>
    </div>
</div>
<!--  //Login  -->
{% endblock %}
```
**[⬆ back to top](#table-of-contents)**

### Login

#### Login View

```python
def login(request):
    if request.method == 'POST':
        # POST일때는 폼 클래스 변수를 만들 때 Post 데이터를 넣어준다.
        form = LoginForm(request.POST)
        if form.is_valid():
            # session 코드가 위치한다.
            request.session['user'] = form.user_id
            return redirect('/')
    else:
        form = LoginForm()

    return render(request, 'login.html', {'form': form})
```

#### Login fomrs

Django에서 제공하는 `form` 객체를 사용하면 view의 코드량을 줄이고 직관적으로 개선할 수 있다.  
`forms.py`라는 파일을 만들고, 아래 `LoginForm`클래스에서 데이터를 검증한다.


```python
from django import forms
from .models import Fcuser
from django.contrib.auth.hashers import check_password

class LoginForm(forms.Form):
    username = forms.CharField(
        error_messages={
            'required': '아이디를 입력해주세요'
        },
        max_length=32, label="사용자 이름")
    password = forms.CharField(
        error_messages={
            'required': '비밀번호를 입력해주세요'
        },
        widget=forms.PasswordInput, label="비밀번호")
    # 비밀번호를 패스워드 타입으로 만들기 위해선 위젯을 직접 지정해야 한다.

    # 비밀번호 일치여부 확인하는 코드
    def clean(self):
        cleaned_data = super().clean() # 값이 들어있지 않으면 여기서 실패처리해서 나간다.
        # 값이 들어왔다는 검증이 끝나면 값을 가지고 온 후에
        username = cleaned_data.get('username')
        password = cleaned_data.get('password')

        if username and password:
            fcuser = Fcuser.objects.get(username=username)
            if not check_password(password, fcuser.password):
                self.add_error('password', '비밀번호가 틀렸습니다.') # 특정 필드에 에러를 넣는 함수
            else:
                self.user_id = fcuser.id # 이렇게 하면 self를 통해서 클래스 변수로 들어가고 밖에서도 접근할 수 있게 된다.

```

#### Login Template


장고에서 관리해주는 `form` 객체는 form에서 필요한 것들을 기본적으로 만들어준다.
`form` 객체의 태그는 장고가 자동으로 생성해주고, 사용자의 입력값을 자동으로 검증해준다.

커스터 마이징이 가능한 것인가..!?라는 의문이 들었지만 커스터 마이징이 가능함!
> 아직 어느 정도까지 커스터마이징이 가능한지는 모름
`as_p` 를 하면 항목 하나하나를 p태그로 감쌈
마찬가지로 `as_table` 등 여러가지 태그로 감싸는 기능이 있다

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
        {{ info_error }}
        {{ password_error }}
        {{ password_valid }}
    </div>
</div>

<div class="row mt-5">
    <div class="col-12">
        <form method="post" action=".">
            {% csrf_token %}
            {% for field in form %}
                <div class="form-group">
                    <label for="{{ field.id_for_label }}">{{ field.label }}</label>
                    <input type="{{ field.field.widget.input_type }}" class="form-control" id="{{ field.id_for_label }}"
                           placeholder="{{ field.label }}" name="{{ field.name }}" />
                </div>
                {% if field.errors %}
                    <span style="color: red">{{ field.errors }}</span>
                {% endif %}
            {% endfor %}
          <button type="submit" class="btn btn-primary">로그인</button>
        </form>
    </div>
</div>
<!--  //Login  -->
{% endblock %}
```



**[⬆ back to top](#table-of-contents)**



