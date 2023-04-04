# Django Authentication System

사용자 인증과 관련된 기능을 모아 놓은 시스템으로 인증, 권한 부여를 함께 제공 및 처리

![django_authentication_system1](django_authentication_system1.png)

## Accounts App 생성

```python
# accounts/urls.py

from django.urls import path
from . import views

app_name = 'accounts'
urlpatterns = [

]
```

```python
# project/urls.py

urlpatterns = [
    ...,
    path('accounts/', include('accounts.urls')),
]
```

## Custom User Model

Django 에서 기본적으로 제공하는 User Model 은 내장된 auth 모듈의 User 클래스 사용

별도 설정없이 사용 할 수 있으나 custom 불가

makemigrations 이후에는 변경 불가하므로 사전에 작업 필수

```python
# accounts/models.py

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

```python
# settings.py

AUTH_USER_MODEL = 'accounts.User'
# 기본 값은 auth.User
```

```python
# accounts/admin.py

from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

## Login

```python
# accounts/urls.py

app_name = 'accounts'
urlpatterns = [
    path('login/', views.login, name='login'),
]
```

```python
# accounts/views.py

from django.contrib.auth.forms import AuthenticationForm
from django.shortcuts import render, redirect
from django.contrib.auth import login as auth_login


def login(request):
    if request.method == 'POST':
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())
            return redirect('accounts:index')
    else:
        form = AuthenticationForm()
    context = {
        'form': form,
    }
    return render(request, 'accounts/login.html', context)
```

```html
<!-- accounts/login.html -->

<h1>로그인</h1>
<form action="{% url 'accounts:login' %}" method="POST">
  {% csrf_token %}
  {{ form.as_p }}
  <input type="submit">
</form>
```

```html
<!-- accounts/index.html -->

<h1>index</h1>
<a href="{% url 'accounts:login' %}">Login</a>
```

![django_authentication_system2](django_authentication_system2.png)

## Logout

```python
# accounts/urls.py

app_name = 'accounts'
urlpatterns = [
    path('login/', views.login, name='login'),
    path('logout/', views.logout, name='logout'),
]
```

```python
# accounts/views.py

from django.contrib.auth import logout as auth_logout

def logout(request):
    auth_logout(request)
    return redirect('accounts:index')
```

```html
<!-- accounts/index.html -->

<h3>Hello, {{ user }}</h3>  <!-- 현재 로그인 유저 정보 출력 -->
<a href="{% url 'accounts:login' %}">Login</a>
<form action="{% url 'accounts:logout' %}" method="POST">
  {% csrf_token %}
  <input type="submit" value="Logout">
</form>
```

![django_authentication_system3](django_authentication_system3.png)
