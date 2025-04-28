# Rule-based Sentiment Analysis

## Rule-based Sentiment Analysis 란

미리 정해진 규칙이나 단어 리스트를 기반으로 텍스트의 감정을 분석하는 방식

```python
from textblob import TextBlob
# TextBlob returns a score between -1 and 1, where negative scores indicate negative sentiment, and positive scores indicate positive sentiment.

sentence_1 = "i had a great time at the movie it was really funny"


sentiment_score = TextBlob(sentence_1)
print(sentiment_score.sentiment.polarity)
```

```output
0.525
```

```python
sentence_2 = "i had a great time at the movie but the parking was terrible"
sentiment_score_2 = TextBlob(sentence_2)

print(sentiment_score_2.sentiment.polarity)

```

```output
-0.09999999999999998
```

```python
sentence_3 = "i went to see a movie"
sentiment_score_3 = TextBlob(sentence_3)

print(sentiment_score_3.sentiment.polarity)
```

```output
0.0
```
