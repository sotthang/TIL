# Pre-trained Transformer Models

## Transformer 란

텍스트를 한 단어씩 처리하지 않고 전체 문맥을 한꺼번에 Attention 메커니즘으로 이해하는 구조

## Pre-trained

대규모 텍스트 등을 사용하여 미리 학습시킴

## Pre-trained Transformer Models 종류

|모델 이름	|설명|
|-|-|
|BERT	|문장의 양방향 문맥을 이해하는 모델|
|GPT	|문장을 생성하는 데 특화된 모델|
|RoBERTa	|BERT를 더 오래 학습시켜 성능을 높인 버전|
|T5	|모든 NLP 작업을 텍스트 생성 문제로 변환해서 푸는 모델|
|DistilBERT	|BERT를 경량화한 모델 (빠르고 가벼움)|

```python
from transformers import pipeline

sentiment_pipeline = pipeline("sentiment-analysis")
text = "I love studying with transformers!"
result = sentiment_pipeline(text)

print(result)
```

```output
[{'label': 'POSITIVE', 'score': 0.9998}]
```
