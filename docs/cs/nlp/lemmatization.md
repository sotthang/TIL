# Lemmatization

## Lemmatization (표제어 추출) 이란

Stemming 은 단어의 마지막 몇 글자를 제거하는 반면, Lemmatization 은 단어를 더 의미 있는 기본형으로 어간화하여 의미를 잃지 않도록 함

단어의 맥락을 포함하는 미리 정의된 사전을 참조하여 단어를 기본형으로 약화시키는 방식

```python
import nltk
nltk.download('wordnet')
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()
```

```python
connect_tokens = ['connecting', 'connected', 'connectivity', 'connect', 'connects']
for t in connect_tokens:
    print(t, " : ", lemmatizer.lemmatize(t))
```

```output
connecting  :  connecting
connected  :  connected
connectivity  :  connectivity
connect  :  connect
connects  :  connects
```

```python
learn_tokens = ['learned', 'learning', 'learn', 'learns', 'learner', 'learners']
for t in learn_tokens:
    print(t, " : ", lemmatizer.lemmatize(t))
```

```output
learned  :  learned
learning  :  learning
learn  :  learn
learns  :  learns
learner  :  learner
learners  :  learner
```

```python
likes_tokens = ['likes', 'better', 'worse']
for t in likes_tokens:
    print(t, " : ", lemmatizer.lemmatize(t))
```

```output
likes  :  like
better  :  better
worse  :  worse
```
