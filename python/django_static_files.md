# Django Static Files

서버에서 제공되는 이미지, JS, CSS 등의 파일

## 기본 경로

app/static

![django_static_files1](django_static_files1.png)

```html
<!-- articles/index.html -->

{% load static %}

<img src="{% static 'articles/sample-1.png' %}" alt="img">
```

## 추가 경로

```python
# settings.py

STATICFILES_DIRS = [
    BASE_DIR / 'static',
]
# 추가 경로 목록을 정의하는 리스트
```

![django_static_files2](django_static_files2.png)

```html
<!-- articles/index.html -->

{% load static %}

<img src="{% static 'sample-2.png' %}" alt="img">
```
