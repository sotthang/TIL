# Django Rest Framework

## Rest (Representational State Transfer)

API Server 개발을 위한 일종의 소프트웨어 설계 방법론

자원을 정의하고 자원에 대한 주소를 지정하는 전반적인 방법 서술

1. 자원 식별
    - URI
2. 자원 행위
    - HTTP Methods
3. 자원 표현
    - JSON 등 최종적으로 표현되는 결과물 (데이터)

## Rest API

Rest 라는 API 디자인 아키텍처를 구현한 API

## DRF Single Model

'''cmd
pip install djangorestframework
'''

HTTP Method

- POST : Create
- GET : Read
- PUT : Update
- Delete : Delete

```python
# config/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/v1/articles/', include('articles.urls')),
]
```

```python
# articles/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('', views.article_list),
    path('<int:article_pk>', views.article_detail),
]
```

```python
# articles/models.py

from django.db import models


class Article(models.Model):
    title = models.CharField(max_length=50)
    content = models.TextField()

```

```python
# articles/serializers.py

from rest_framework import serializers
from .models import Article


class ArticleSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = '__all__'


class ArticleListSerializer(serializers.ModelSerializer):
    class Meta:
        model = Article
        fields = ('id', 'title',)
```

```python
# articles/views.py

from django.shortcuts import render
from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import Article
from . serializers import ArticleSerializer, ArticleListSerializer
from rest_framework import status


@api_view(['GET', 'POST'])
def article_list(request):
    if request.method == 'GET':
        articles = Article.objects.all()
        serializer = ArticleListSerializer(articles, many=True)
        return Response(serializer.data)
    elif request.method == 'POST':
        serializer = ArticleSerializer(data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data, status=status.HTTP_201_CREATED)


@api_view(['GET', 'DELETE', 'PUT'])
def article_detail(request, article_pk):
    article = Article.objects.get(pk=article_pk)
    if request.method == 'GET':
        serializer = ArticleSerializer(article)
        return Response(serializer.data)
    elif request.method == 'DELETE':
        article.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)
    elif request.method == 'PUT':
        serializer = ArticleSerializer(article, data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)
```

### API Test

```cmd
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

Postman 활용 (https://www.postman.com/)

### POST

![django_rest_framework1](django_rest_framework1.png)

### GET

![django_rest_framework2](django_rest_framework2.png)

### PUT

![django_rest_framework3](django_rest_framework3.png)

### DELETE

![django_rest_framework4](django_rest_framework4.png)

## DRF N:1 Model

```python
# articles/urls.py

urlpatterns = [
    ...,
    path('comments/', views.comment_list),
    path('comments/<comment_pk>/', views.comment_detail),
    path('<int:article_pk>/comments/', views.comment_create),
    path('index', views.index, name='index'),
]
```

```python
# articles/models.py

class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE, related_name='comments')
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

```cmd
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```


```python
# articles/serializers.py

class CommentSerializer(serializers.ModelSerializer):
    class Meta:
        model = Comment
        fields = '__all__'
        read_only_fields = ('article',)


class ArticleSerializer(serializers.ModelSerializer):
    class MyCommentSerializer(serializers.ModelSerializer):
        class Meta:
            model = Comment
            fields = ('id', 'article', 'content',)

    comment_set = CommentSerializer(many=True, read_only=True)
    comment_count = serializers.IntegerField(source='comment_set.count', read_only=True)
    
    class Meta:
        model = Article
        fields = '__all__'
        read_only_fields = ('comment_set', 'comment_count',)
```

```python
# articles/views.py

@api_view(['GET'])
def comment_list(request):
    comments = Comment.objects.all()
    serializer = CommentSerializer(comments, many=True)
    return Response(serializer.data)


@api_view(['GET' ,'DELETE', 'PUT'])
def comment_detail(request, comment_pk):
    comment = Comment.objects.get(pk=comment_pk)
    if request.method == 'GET':
        serializer = CommentSerializer(comment)
        return Response(serializer.data)
    elif request.method == 'DELETE':
        comment.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)
    elif request.method == 'PUT':
        serializer = CommentSerializer(comment, data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)


@api_view(['POST'])
def comment_create(request, article_pk):
    article = Article.objects.get(pk=article_pk)
    serializer = CommentSerializer(data=request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save(article=article)
        return Response(serializer.data, status=status.HTTP_201_CREATED)
```
