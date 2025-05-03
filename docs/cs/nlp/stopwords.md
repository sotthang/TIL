# Stopwords

## Stopwords (불용어) 란

불용 목록(부정 사전)에 있는 단어로, 자연어 데이터(텍스트) 처리 전후에 중요하지 않기 때문에 필터링(즉, 정지)

ex: "to", "and", "a", "of"

stopwords 를 제거하는 이유는 복잡성을 크게 줄이기 위함

텍스트에 큰 의미를 부여하지 않기 때문에, 이를 제거하면 더 작고 깔끔한 데이터셋을 얻을 수 있음

더 작고 깔끔한 데이터셋은 머신러닝의 정확도를 높이고 처리 시간을 단축시키는데 도움이 됨

```python
import nltk
nltk.download('stopwords')
from nltk.corpus import stopwords

en_stopwords = stopwords.words('english')

print(en_stopwords)
```

```output
['i', 'me', 'my', 'myself', 'we', 'our', 'ours', 'ourselves', 'you', "you're", "you've", "you'll", "you'd", 'your', 'yours', 'yourself', 'yourselves', 'he', 'him', 'his', 'himself', 'she', "she's", 'her', 'hers', 'herself', 'it', "it's", 'its', 'itself', 'they', 'them', 'their', 'theirs', 'themselves', 'what', 'which', 'who', 'whom', 'this', 'that', "that'll", 'these', 'those', 'am', 'is', 'are', 'was', 'were', 'be', 'been', 'being', 'have', 'has', 'had', 'having', 'do', 'does', 'did', 'doing', 'a', 'an', 'the', 'and', 'but', 'if', 'or', 'because', 'as', 'until', 'while', 'of', 'at', 'by', 'for', 'with', 'about', 'against', 'between', 'into', 'through', 'during', 'before', 'after', 'above', 'below', 'to', 'from', 'up', 'down', 'in', 'out', 'on', 'off', 'over', 'under', 'again', 'further', 'then', 'once', 'here', 'there', 'when', 'where', 'why', 'how', 'all', 'any', 'both', 'each', 'few', 'more', 'most', 'other', 'some', 'such', 'no', 'nor', 'not', 'only', 'own', 'same', 'so', 'than', 'too', 'very', 's', 't', 'can', 'will', 'just', 'don', "don't", 'should', "should've", 'now', 'd', 'll', 'm', 'o', 're', 've', 'y', 'ain', 'aren', "aren't", 'couldn', "couldn't", 'didn', "didn't", 'doesn', "doesn't", 'hadn', "hadn't", 'hasn', "hasn't", 'haven', "haven't", 'isn', "isn't", 'ma', 'mightn', "mightn't", 'mustn', "mustn't", 'needn', "needn't", 'shan', "shan't", 'shouldn', "shouldn't", 'wasn', "wasn't", 'weren', "weren't", 'won', "won't", 'wouldn', "wouldn't"]
```

```python
sentence = "it was too far to go to the shop and he did not want her to walk"
sentance_no_stopwords = ' '.join([word for word in sentence.split() if word not in (en_stopwords)])

print(sentance_no_stopwords)
```

```output
far go shop want walk
```

```python
en_stopwords.remove("not")
en_stopwords.append("go")

sentance_no_stopwords_custom = ' '.join([word for word in sentence.split() if word not in (en_stopwords)])

print(sentance_no_stopwords_custom)
```

```output
far shop did not want walk
```
