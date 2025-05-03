# Tokenizing Text

NLP 의 기본 단계는 토큰화라는 과정을 통해 텍스트를 더 작은 단위 (토큰)로 변환

단어 토큰화는 가장 일반적인 토큰화 형태로 텍스트의 개별 단어가 토큰이 되지만, 사용 사례에 따라 문장, 하위 단어 또는 개별 문자가 토큰이 될 수도 있음

```python
import nltk
nltk.download('punkt_tab')
from nltk.tokenize import word_tokenize, sent_tokenize
```

## Sentance Tokenization

```python
sentences = "Her cat's name is Luna. Her dog's name is max"
sent_tokenize(sentences)
```

```output
["Her cat's name is Luna.", "Her dog's name is max"]
```

## Word Tokenization

```python
sentence = "Her cat's name is Luna and her dog's name is max"
word_tokenize(sentence)
```

```output
['Her',
 'cat',
 "'s",
 'name',
 'is',
 'Luna',
 'and',
 'her',
 'dog',
 "'s",
 'name',
 'is',
 'max']
```

1. cat's 가 cat 과 's 로 분리됨에 주의
2. her 과 Her 은 같은 의미이지만 토큰은 다른 것으로 처리됨에 주의 (lowercase 의 이유)
