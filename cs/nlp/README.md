# NLP (Natural Language Processing, 자연어 처리)

## NLP 란

사람이 사용하는 언어인 자연어를 컴퓨터가 이해하고 처리할 수 있도록 하는 인공지능의 하위 분야

## 자연어 처리 기술

1. 텍스트 전처리 : NLP의 첫 번째 단계는 텍스트 전처리입니다. 이 단계에서는 원시 텍스트를 기계가 처리할 수 있는 형태로 변환합니다. 주요 작업에는 다음과 같은 것들이 포함될 수 있문장을 단어,구 또는 문장으로 나누는 작업입니다. 불용어 제거 (Stopword Removal): 의미를 거의 갖지 않는 단어(예: 'the', 'and', 'is' 등)를 제거합니다. 정규화(Normalization):  단어들을 표준화하여 다른 형태의 동일한 단어들을 하나로 통일시킵니다

2. 형태소 분석과 구문 분석:  형태소 분석(Morphological  Analysis): 단어의 형태소를 분석하여 어간 추출이나 원형 복원을 수행합니다. 구문 분석(Syntax  Parsing): 문장의 구조를 이해하고, 문법적인 구조를 분석하여 문장의 의미를 파악합니다.

3. 의미 분석‍ : 문맥을 이해하고 단어나 문장의 의미를 추론하는 작업입니다. 최근에는 단어 임베딩(Word Embedding) 기법을 활용하여 단어들을 벡터 공간에 매핑하여 의미적 유사성을 계산하는 방법이 주로 사용됩니다.

4. 기계 학습과 딥 러닝 : NLP에서 기계 학습과 딥 러닝 기술이 중요한 역할을 합니다. 다음은 일반적으로 사용되는 몇 가지 기법입니다.‍
    1. 통계 기반 기법: N-gram 모델, 통계적 언어 모델 등을 사용하여 문장을 생성하거나 분석합니다.
    2. 기계 학습 기반 접근: SVM(Support Vector Machine), 나이브 베이즈(Naive Bayes) 등의 분류 알고리즘을 사용하여 텍스트를 분류하거나 정보 추출 작업을 수행합니다.‍
    3. 딥 러닝 기반 접근: 순환 신경망(RNN), 장단기 메모리(LSTM),  변환자(Transformer) 등의 신경망 구조를 사용하여 문장의 의미를 이해하고 생성하는 작업을 수행합니다. 특히 최근의 대부분의 NLP 최고 성능 모델들은 딥 러닝 기반의 Transformer 아키텍처를 기반으로 합니다.

## Supervised NLP vs Unsupervised NLP

### Supervised NLP

입력 데이터와 그에 해당하는 레이블(정답)이 있는 경우에 사용

주어진 데이터를 바탕으로 정답과 일치하는 패턴을 학습하고, 새로운 데이터에 대해 올바른 출력을 예측

- 주요 목적 
    - 정답이 주어진 상태에서 데이터를 학습하여 미래의 입력에 대한 예측을 정확하게 수행하는 것
- 주요 알고리즘
    - 분류(Classification): 데이터가 특정 카테고리에 속하는지 예측하는 문제 (ex: 스팸 메일 필터링, 질병 진단)
    - 회귀(Regression): 연속적인 값을 예측하는 문제 (ex: 주택 가격 예측, 온도 예측)

### Unsupervised NLP

입력 데이터에 레이블(정답)이 없는 경우에 사용

데이터의 숨겨진 패턴이나 구조를 찾는 것이 목적입

- 주요 목적
    - 정답 없이 데이터 간의 관계나 패턴을 발견하고, 비슷한 데이터끼리 그룹화하거나 데이터의 분포를 분석하는 것
- 주요 알고리즘:
    - 군집화(Clustering): 비슷한 데이터끼리 그룹을 만드는 문제 (ex: 고객 세분화, 이미지 분류)
    - 차원 축소(Dimensionality Reduction): 데이터를 더 작은 차원으로 변환하면서 중요한 정보를 유지하는 방법 (ex: 주성분 분석(PCA), t-SNE)

### 분류(Classification) vs 군집화(Clustering)

분류(Classification) - 감독학습
- 정답(레이블)이 있는 데이터를 학습
- 입력 데이터를 사전에 정의된 클래스 중 하나로 분류
- ex: 고양이와 개 이미지를 분류하거나, 고객의 신용 위험을 예측하는 문제

군집화(Clustering) - 비지도학습
- 정답(레이블)이 없는 데이터를 학습합
- 입력 데이터를 비슷한 특성을 가진 그룹(클러스터)으로 묶음음
- ex: 비슷한 고객을 그룹화하여 마케팅 전략을 세우거나, 유사한 뉴스 기사를 묶는 문제


## 참고 문헌

- https://www.thumb.is/korean-blog-posts/what-is-nlp
- https://nlp2024.tistory.com/120

## 리스트
- Text Processing
    - [Lowercase](https://github.com/sotthang/TIL/blob/main/cs/nlp/lowercase.md)
    - [Stopwords](https://github.com/sotthang/TIL/blob/main/cs/nlp/stopwords.md)
    - [Regular Expressions](https://github.com/sotthang/TIL/blob/main/cs/nlp/regular_expressions.md)
    - [Tokenizing Text](https://github.com/sotthang/TIL/blob/main/cs/nlp/tokenizing_text.md)
    - [Stemming](https://github.com/sotthang/TIL/blob/main/cs/nlp/stemming.md)
    - [Lemmatization](https://github.com/sotthang/TIL/blob/main/cs/nlp/lemmatization.md)
    - [N-grams](https://github.com/sotthang/TIL/blob/main/cs/nlp/n-grams.md)
- Identifying parts of speech and named entities
    - [Text Tagging](https://github.com/sotthang/TIL/blob/main/cs/nlp/text_tagging.md)
    - [Parts of Speech (POS) tagging](https://github.com/sotthang/TIL/blob/main/cs/nlp/pos.md)
    - [Named Entity Recognition](https://github.com/sotthang/TIL/blob/main/cs/nlp/ner.md)
- Sentiment Analysis
    - [Sentiment Analysis](https://github.com/sotthang/TIL/blob/main/cs/nlp/sentiment_analysis.md)
    - [Rule-based Sentiment Analysis](https://github.com/sotthang/TIL/blob/main/cs/nlp/rule-based_sentiment_analysis.md)
    - [Pre-trained Transformer Models](https://github.com/sotthang/TIL/blob/main/cs/nlp/pre-trained_transformer_models.md)
- Vectorizing Text
    - [Vectorizing Text](https://github.com/sotthang/TIL/blob/main/cs/nlp/vectorizing_text.md)
    - [Bag of Words (BoW)](https://github.com/sotthang/TIL/blob/main/cs/nlp/bow.md)
    - [TF-IDF (Term Frequency-Inverse Document Frequency)](https://github.com/sotthang/TIL/blob/main/cs/nlp/tf-idf.md)
- Topic Modeling
    - [Topic Modeling](https://github.com/sotthang/TIL/blob/main/cs/nlp/topic_modeling.md)
    - [LDA (Latent Dirichlet Allocation)](https://github.com/sotthang/TIL/blob/main/cs/nlp/lda.md)
    - [LSA (Latent Semantic Analysis)](https://github.com/sotthang/TIL/blob/main/cs/nlp/lsa.md)
- Text Classifier
    - [Logistic Regression](https://github.com/sotthang/TIL/blob/main/cs/nlp/logistic_regression.md)
    - [Naive Bayes](https://github.com/sotthang/TIL/blob/main/cs/nlp/naive_bayes.md)
    - [Linear Support Vector Machine](https://github.com/sotthang/TIL/blob/main/cs/nlp/lsvm.md)
