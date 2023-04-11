# Django Many to One Relationship

하나의 테이블에서 0개 이상의 레코드가 다른 테이블의 레코드 한 개와 관련된 관계

N:1 or 1:N

article(1) - comment(N) : 1개의 게시글에는 0개 이상의 댓글을 작성 가능

comment

|id|
|-|
|content|
|created_at|
|updated_at|
|article_id|

article

|id|
|-|
|title|
|content|
|created_at|
|updated_at|

## comment 설정

```python
# articles/models.py

class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    # ForeignKey(참조 모델 class 이름, 참조 모델 class 삭제 시 동작 방법)
    # CASCADE - 참조 된 객체가 삭제 됐을 때 같이 삭제
    content = models.CharField(max_length=200)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

```cmd
python manage.py makemigrations
python manage.py migrate
```

## 댓글 작성 및 출력

```python
# articles/forms.py

from .models import Article, Comment

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        fields = ('content',)
        # article 은 사용자에게 입력 받는 것이 아닌 view 함수 내에서 별도 처리
```

```python
# articles/views.py

from .forms import ArticleForm, CommentForm

def detail(request, pk):
    article = Article.objects.get(pk=pk)
    comment_form = CommentForm()
    comments = article.comment_set.all()
    context = {
        'article': article,
        'comment_form': comment_form,
        'comments': comments,
    }
    return render(request, 'articles/detail.html', context)


def comments_create(request, pk):
    article = Article.objects.get(pk=pk)
    comment_form = CommentForm(request.POST)
    if comment_form.is_valid():
        comment = comment_form.save(commit=False)
        comment.article = article
        comment_form.save()
        return redirect('articles:detail', article.pk)
    context = {
        'article': article,
        'comment_form': comment_form,
    }
    return render(request, 'article/detail.html', context)
```


```python
# articles/urls.py

urlpatterns = [
    ...
    path('<int:pk>/commments/', views.comments_create, name='comments_create'),
]
```

```html
<!-- articles/detail.html -->

<form action="{% 'articles:comments_create' article.pk %}" method="POST">
    {% csrf_token %}
    {{ comment_form }}
    <input type="submit">
</form>

<ul>
  {% for comment in comments %}
    <li>{{ comment.content }}</li>
  {% endfor %}
</ul>
```

## 댓글 삭제

```python
# articles/urls.py

urlpatterns = [
    ...
    path('<int:pk>/commments/<int:comment_pk>/delete/', views.comments_delete, name='comments_delete'),
]
```

```python
# articles/views.py

def comments_delete(request, article_pk, comment_pk):
    comment = Comment.objects.get(pk=comment_pk)
    comment.delete()
    return redirect('articles:detail', article_pk)
```

```html
<!-- articles/detail.html -->

<ul>
  {% for comment in comments %}
    <li>
      {{ comment.content }}
      <form action="{% 'articles:comments_delete' article.pk comment.pk %}" method="POST">
        {% csrf_token %}
        <input type="submit" value="DELETE">
      </form>
    </li>
  {% endfor %}
</ul>
```
