# LSA

## LSA (Latent Semantic Analysis) 란

문서와 단어 사이의 관계를 수학적으로 분석해서, 단어들 사이의 의미적 유사성이나 문서들의 주제 구조를 파악하는 방법

BoW나 TF-IDF로 만든 희소한 행렬을 기반으로, 차원을 축소(SVD)해서 잠재적인 의미 공간(latent semantic space)을 추출하는 게 핵심

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.decomposition import TruncatedSVD

docs = [
    "cat dog apple",
    "dog orange banana",
    "apple orange fruit"
]

vectorizer = TfidfVectorizer()
X = vectorizer.fit_transform(docs)

lsa = TruncatedSVD(n_components=2)
X_lsa = lsa.fit_transform(X)

print(X_lsa)
```

```output
[[ 7.15623251e-01 -3.09916607e-17]
 [ 7.15623251e-01 -6.04907035e-01]
 [ 7.15623251e-01  6.04907035e-01]]
```
