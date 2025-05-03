# LDA

## LDA (Latent Dirichlet Allocation) 란

문서와 단어 간의 잠재된 주제 분포(latent topics)를 추정

LDA는 다음과 같은 전제를 기반으로 작동

1. 문서는 여러 개의 주제(topic)로 이루어져 있음
2. 각 주제는 특정 단어들의 분포(distribution)를 따름
3. 문서에 포함된 단어들은 문서가 가진 주제들의 조합으로 생성됨

LDA를 문서 집합에 적용하면

-  각 문서가 어떤 주제들로 이루어져 있는지 (예: 문서1은 주제1이 70%, 주제2가 30%)
- 각 주제가 어떤 단어들로 구성되어 있는지 (예: 주제1은 '경제', '금리', '주식' 등이 높은 확률로 등장)

```python
from gensim import corpora, models

documents = [
    "I play football and basketball",
    "Government passed a new policy",
    "The team scored a goal"
]

texts = [doc.lower().split() for doc in documents]
dictionary = corpora.Dictionary(texts)
corpus = [dictionary.doc2bow(text) for text in texts]
lda_model = models.LdaModel(corpus, num_topics=2, id2word=dictionary, passes=10)
topics = lda_model.print_topics()

for topic in topics:
    print(topic)
```

```output
(0, '0.124*"football" + 0.124*"play" + 0.124*"and" + 0.124*"basketball" + 0.124*"i" + 0.043*"a" + 0.042*"policy" + 0.042*"passed" + 0.042*"the" + 0.042*"government"')
(1, '0.147*"a" + 0.088*"scored" + 0.088*"team" + 0.088*"goal" + 0.088*"new" + 0.088*"government" + 0.088*"the" + 0.088*"passed" + 0.088*"policy" + 0.030*"i"')
```