# Naive Bayes

## Naive Bayes 란

확률 기반의 지도 학습 분류 알고리즘

이름 그대로 순진한(Naive) 가정을 기반으로 하는데, 특성(feature) 간의 독립성을 가정한다는 점이 핵심

NLP 에서 특히 자주 쓰이는 이유는 속도가가 빠르고, 적은 데이터로도 잘 작동 (ex: 스팸 필터, 감정 분석)


- Multinomial Naive Bayes: 가장 흔하며 텍스트 분류에 자주 사용, 단어의 등장 횟수 기반
- Bernoulli Naive Bayes: 단어가 등장했는지만 고려 (이진 특성)
- Gaussian Naive Bayes: 연속형 데이터 (예: 숫자 센서값 등)

장점
- 매우 빠름
- 적은 데이터에도 잘 작동
- 고차원 데이터(=많은 단어)에도 효과적

단점
- 특성 독립 가정이 현실적이지 않음
- 연속형 데이터에는 부적합 (텍스트에는 잘 맞음)

```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report
from sklearn.naive_bayes import MultinomialNB

data = pd.DataFrame([("i love spending time with my friends and family", "positive"),
                     ("that was the best meal i've ever had in my life", "positive"),
                     ("i feel so grateful for everything i have in my life", "positive"),
                     ("i received a promotion at work and i couldn't be happier", "positive"),
                     ("watching a beautiful sunset always fills me with joy", "positive"),
                     ("my partner surprised me with a thoughtful gift and it made my day", "positive"),
                     ("i am so proud of my daughter for graduating with honors", "positive"),
                     ("listening to my favorite music always puts me in a good mood", "positive"),
                     ("i love the feeling of accomplishment after completing a challenging task", "positive"),
                     ("i am excited to go on vacation next week", "positive"),
                     ("i feel so overwhelmed with work and responsibilities", "negative"),
                     ("the traffic during my commute is always so frustrating", "negative"),
                     ("i received a parking ticket and it ruined my day", "negative"),
                     ("i got into an argument with my partner and we're not speaking", "negative"),
                     ("i have a headache and i feel terrible", "negative"),
                     ("i received a rejection letter for the job i really wanted", "negative"),
                     ("my car broke down and it's going to be expensive to fix", "negative"),
                     ("i'm feeling sad because i miss my friends who live far away", "negative"),
                     ("i'm frustrated because i can't seem to make progress on my project", "negative"),
                     ("i'm disappointed because my team lost the game", "negative")
                    ],
                    columns=['text', 'sentiment'])

data = data.sample(frac=1).reset_index(drop=True)

X = data['text']
y = data['sentiment']

# text vectorization to bow - CountVectorizer
countvec = CountVectorizer()
countvec_fit = countvec.fit_transform(X)
bag_of_words = pd.DataFrame(countvec_fit.toarray(), columns = countvec.get_feature_names_out())

X_train, X_test, y_train, y_test = train_test_split(bag_of_words, y, test_size=0.3, random_state = 7)

nb = MultinomialNB().fit(X_train, y_train)

y_pred_nb = nb.predict(X_test)

print(classification_report(y_test, y_pred_nb, zero_division=0))
```

```output
                precision   recall   f1-score    support

    negative       0.50      0.50      0.50         2
    positive       0.75      0.75      0.75         4

    accuracy                           0.67         6
   macro avg       0.62      0.62      0.62         6
weighted avg       0.67      0.67      0.67         6
```
