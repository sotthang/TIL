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

## 참고 문헌

- https://www.thumb.is/korean-blog-posts/what-is-nlp


## 리스트

- [Lowercase](https://github.com/sotthang/TIL/blob/main/cs/nlp/lowercase.md)
- [stopwords](https://github.com/sotthang/TIL/blob/main/cs/nlp/stopwords.md)
