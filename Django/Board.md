# Board


## Table of Contents

  1. [Settings](#Settings)
  1. [BaseTemplate](#BaseTemplate)
  1. [Board Model](#Board-Model)
  1. [Board View](#Board-View)
  1. [Board Template](#Board-Template)
  


---

## Settings

### Add Application 
`settings.py`에서 사용할 애플리케이션 등록

```python
INSTALLED_APPS = [
    'board',
]
```

### URL and View Mapping

```python
from django.contrib import admin
from django.urls import path, include
from fcuser.views import home

urlpatterns = [
    path('board/', include('board.urls')),
]
```

```python
from django.urls import path
from . import views

urlpatterns = [
    path('list', views.board_list, name='board_list'),
]
```

### admin 

```python
from django.contrib import admin
from .models import Board

# Register your models here.
class BoardAdmin(admin.ModelAdmin):
    list_display = ('title', )
    # 리스트에는 타이틀만 나오게

admin.site.register(Board, BoardAdmin) # 보드어드민 연결
```

### apps

자동으로 등록이 되는 것 같은데?


**[⬆ back to top](#table-of-contents)**


## BaseTemplate
### MVT의 T를 확장하여 상속하기

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Base</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
<!--    <link rel="stylesheet" href="/static/bootstrap.min.css" />-->
    <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>

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
**[⬆ back to top](#table-of-contents)**


## Board Model

```python
from django.db import models

class Board(models.Model):
    title = models.CharField(max_length=128, verbose_name='제목')
    contents = models.TextField(verbose_name='내용') # 길이에 제한이 없음
    writer = models.ForeignKey('user.User', on_delete=models.CASCADE, verbose_name='작성자')
    # ForeignKey를 통해 연결
    # 사용자가 탈퇴할 경우..! 작성자가 사용한 글들은...! 글들에 대한 정책
    # CASCADE를 통해 작성자가 작성한 글을 같이 삭제하는 설정
    registered_dttm = models.DateTimeField(auto_now_add=True, verbose_name='등록시간')

    def __str__(self):
        return self.title

    class Meta:
        db_table = 'board'
        verbose_name = '게시글'
        verbose_name_plural = '게시글'
```




**[⬆ back to top](#table-of-contents)**


## Board View

`boards` 필드를 통해서 board 를 가져온 다음 단축함수 render를 통해 Template 으로 전달한다.
`Board.objects.all().order_by`의 메서드로 dash(-)가 포함된 값을 전달하면 역순 정렬(내림차순)을 의미한다. 

```python
from django.shortcuts import render
from .models import Board
# Create your views here.

def board_list(request):
    boards = Board.objects.all().order_by('-id') 
    return render(request, 'board_list.html', {'boards': boards})

```

**[⬆ back to top](#table-of-contents)**



## Board Template









