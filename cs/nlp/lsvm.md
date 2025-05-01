# Linear Support Vector Machine

## Linear Support Vector Machine 란

지도 학습 분류 알고리즘으로, 특히 이진 분류 문제에 특화

NLP에서 감정 분석, 스팸 분류, 문서 분류 등에 자주 사용

SVM 은 클래스 간의 "최적의 결정 경계(hyperplane)"를 찾는 것이 목적

이 경계는 두 클래스 사이의 마진(margin)을 최대화하도록 선택

Linear SVM 은 데이터를 선형적으로 나눌 수 있다고 가정함 (즉, 직선/평면으로 분리할 수 있는 경우)

장점
- 고차원(=많은 단어 수)의 희소 데이터에 강함 (텍스트 분류에 최적)
- 일반화 성능이 뛰어남
- 빠르고 효율적 (특히 LinearSVC)

단점
- 확률값 출력이 기본적으로 없음 (predict_proba 안 됨, CalibratedClassifierCV로 보완 가능)
- 비선형 분류에는 부적합 (RBF 커널 등으로 확장 필요)

```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report
from sklearn.linear_model import LogisticRegression, SGDClassifier

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

svm = SGDClassifier().fit(X_train, y_train)

y_pred_svm = svm.predict(X_test)

print(classification_report(y_test, y_pred_svm, zero_division=0))
```

```output
                precision   recall   f1-score    support

    negative       0.00      0.00      0.00         2
    positive       0.50      0.50      0.50         4

    accuracy                           0.33         6
   macro avg       0.25      0.25      0.25         6
weighted avg       0.33      0.33      0.33         6
```
