# Stemming

## Stemming (어간 추출) 이란

전처리의 다음 단계는 텍스트 표준화인데 텍스트 표준화 방법 중 하나가 Stemming

Stemming 은 단어를 기본형으로 환원하는 것 (ex: connecting, connected -> connect)

단어의 접미사/어미를 제거하는 방식이지만, 때로는 기본형이 의미가 없거나 적절한 단어가 아닐 수 있음

이런 방식으로 텍스트 표준화를 하는 이유는 데이터셋에서 고유 단어의 수가 줄어들어 데이터의 크기와 복잡성을 줄이기 위함

데이터에서 복잡성과 노이즈를 제거하는 것은 머신 러닝을 위해 데이터를 준비하는 데 중요한 단계

```python
from nltk.stem import PorterStemmer

ps = PorterStemmer()
```

```python
connect_tokens = ['connecting', 'connected', 'connectivity', 'connect', 'connects']
for t in connect_tokens:
    print(t, " : ", ps.stem(t))
```

```output
connecting  :  connect
connected  :  connect
connectivity  :  connect
connect  :  connect
connects  :  connect
```

```python
learn_tokens = ['learned', 'learning', 'learn', 'learns', 'learner', 'learners']
for t in learn_tokens:
    print(t, " : ", ps.stem(t))
```

```output
learned  :  learn
learning  :  learn
learn  :  learn
learns  :  learn
learner  :  learner
learners  :  learner
```

```python
likes_tokens = ['likes', 'better', 'worse']
for t in likes_tokens:
    print(t, " : ", ps.stem(t))
```

```output
likes  :  like
better  :  better
worse  :  wors
```
