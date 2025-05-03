# N-grams

## N-grams 이란

특정 순서로 인접한 N 개의 기호 시퀀스 (N 개의 연속적인 단어 나열)

텍스트를 N-grams 으로 나누어 전처리 과정을 점검하고, 데이터 내용을 탐색하고, 머신러닝을 위한 새로운 특징을 생성 가능

```python
import nltk
import pandas as pd

tokens = ['the', 'rise', 'of', 'artificial', 'intelligence', 'has', 'led', 'to', 'significant', 'advancements', 'in', 'natural', 'language', 'processing', 'computer', 'vision', 'and', 'other', 'fields', 'machine', 'learning', 'algorithms', 'are', 'becoming', 'more', 'sophisticated', 'enabling', 'computers', 'to', 'perform', 'complex', 'tasks', 'that', 'were', 'once', 'thought', 'to', 'be', 'the', 'exclusive', 'domain', 'of', 'humans', 'with', 'the', 'advent', 'of', 'deep', 'learning', 'neural', 'networks', 'have', 'become', 'even', 'more', 'powerful', 'capable', 'of', 'processing', 'vast', 'amounts', 'of', 'data', 'and', 'learning', 'from', 'it', 'in', 'ways', 'that', 'were', 'not', 'possible', 'before', 'as', 'a', 'result', 'ai', 'is', 'increasingly', 'being', 'used', 'in', 'a', 'wide', 'range', 'of', 'industries', 'from', 'healthcare', 'to', 'finance', 'to', 'transportation', 'and', 'its', 'impact', 'is', 'only', 'set', 'to', 'grow', 'in', 'the', 'years', 'to', 'come']

print(tokens)
```

```output
['the', 'rise', 'of', 'artificial', 'intelligence', 'has', 'led', 'to', 'significant', 'advancements', 'in', 'natural', 'language', 'processing', 'computer', 'vision', 'and', 'other', 'fields', 'machine', 'learning', 'algorithms', 'are', 'becoming', 'more', 'sophisticated', 'enabling', 'computers', 'to', 'perform', 'complex', 'tasks', 'that', 'were', 'once', 'thought', 'to', 'be', 'the', 'exclusive', 'domain', 'of', 'humans', 'with', 'the', 'advent', 'of', 'deep', 'learning', 'neural', 'networks', 'have', 'become', 'even', 'more', 'powerful', 'capable', 'of', 'processing', 'vast', 'amounts', 'of', 'data', 'and', 'learning', 'from', 'it', 'in', 'ways', 'that', 'were', 'not', 'possible', 'before', 'as', 'a', 'result', 'ai', 'is', 'increasingly', 'being', 'used', 'in', 'a', 'wide', 'range', 'of', 'industries', 'from', 'healthcare', 'to', 'finance', 'to', 'transportation', 'and', 'its', 'impact', 'is', 'only', 'set', 'to', 'grow', 'in', 'the', 'years', 'to', 'come']
```

## Unigrams

N 이 1 인 N-grams

```python
unigrams = (pd.Series(nltk.ngrams(tokens, 1)).value_counts()) 

print(unigrams)
```

```output
(to,)          7
(of,)          6
(the,)         4
(in,)          4
(learning,)    3
              ..
(humans,)      1
(rise,)        1
(advent,)      1
(deep,)        1
(come,)        1
Name: count, Length: 79, dtype: int64
```

## Bigrams

N 이 2 인 N-grams

```python
bigrams = (pd.Series(nltk.ngrams(tokens, 2)).value_counts()) 

print(bigrams)
```

```output
(that, were)             2
(the, rise)              1
(increasingly, being)    1
(ai, is)                 1
(result, ai)             1
                        ..
(tasks, that)            1
(complex, tasks)         1
(perform, complex)       1
(to, perform)            1
(to, come)               1
Name: count, Length: 105, dtype: int64
```

### Trigrams

N 이 3인 N-grams

```python
trigrams = (pd.Series(nltk.ngrams(tokens, 3)).value_counts()) 

print(trigrams)
```

```output
(the, rise, of)              1
(even, more, powerful)       1
(ai, is, increasingly)       1
(result, ai, is)             1
(a, result, ai)              1
                            ..
(that, were, once)           1
(tasks, that, were)          1
(complex, tasks, that)       1
(perform, complex, tasks)    1
(years, to, come)            1
Name: count, Length: 105, dtype: int64
```
