# Logistic Regression

## Logistic Regression 란

이진 분류(binary classification) 문제를 해결할 때 자주 사용하는 선형 모델 기반의 지도 학습 알고리즘

텍스트를 기반으로 어떤 문장이 긍정인지 부정인지, 혹은 스팸인지 아닌지 등을 판단할 때 많이 사용

- 입력: 텍스트(문장, 문서 등)를 벡터 형태로 변환한 것 (예: BoW, TF-IDF, Word Embedding 등)
- 출력: 0 또는 1 (예: 스팸 여부, 감정 분석 등)

장점
- 간단하고 빠름
- 해석 가능함 (특성이 결과에 어떻게 영향을 미치는지 파악 가능)
- 작은 데이터셋에도 잘 작동

단점
- 선형 결정 경계만 학습 가능 (복잡한 관계는 잘 못 잡음)
- 특성 엔지니어링이 중요


```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, classification_report

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

lr = LogisticRegression(random_state=1).fit(X_train, y_train)

y_pred_lr = lr.predict(X_test)

print(classification_report(y_test, y_pred_lr, zero_division=0))
```

```output
                 precision  recall   f1-score    support

    negative       0.67      0.50      0.57         4
    positive       0.33      0.50      0.40         2

    accuracy                           0.50         6
   macro avg       0.50      0.50      0.49         6
weighted avg       0.56      0.50      0.51         6
```
