# TF-IDF

## TF-IDF (Term Frequency-Inverse Document Frequency) 란

BoW의 단순한 단어 빈도 계산을 보완해서 중요한 단어에 더 높은 가중치를 부여하는 방식

- 어떤 단어가 한 문서에서 자주 등장하면 중요할 수 있음 (TF(t) = (단어 t의 등장 횟수) / (문서 전체 단어 수)
)
- 그런데 그 단어가 모든 문서에 다 등장한다면 덜 중요함 (IDF(t) = log(전체 문서 수 / (단어 t를 포함한 문서 수 + 1))
)

```python
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
data = [' Most shark attacks occur about 10 feet from the beach since that is where the people are',
        'the efficiency with which he paired the socks in the drawer was quite admirable',
        'carol drank the blood as if she were a vampire',
        'giving directions that the mountains are to the west only works when you can see them',
        'the sign said there was road work ahead so he decided to speed up',
        'the gruff old man sat in the back of the bait shop grumbling to himself as he scooped out a handful of worms']
tfidfvec = TfidfVectorizer()
tfidfvec_fit = tfidfvec.fit_transform(data)
tfidf_bag = pd.DataFrame(tfidfvec_fit.toarray(), columns = tfidfvec.get_feature_names_out())

print(tfidf_bag)
```

```output
         10     about  admirable     ahead       are        as   attacks  \
0  0.257061  0.257061   0.000000  0.000000  0.210794  0.000000  0.257061   
1  0.000000  0.000000   0.293641  0.000000  0.000000  0.000000  0.000000   
2  0.000000  0.000000   0.000000  0.000000  0.000000  0.292313  0.000000   
3  0.000000  0.000000   0.000000  0.000000  0.222257  0.000000  0.000000   
4  0.000000  0.000000   0.000000  0.290766  0.000000  0.000000  0.000000   
5  0.000000  0.000000   0.000000  0.000000  0.000000  0.178615  0.000000   

      back     bait     beach  ...      were     west     when     where  \
0  0.00000  0.00000  0.257061  ...  0.000000  0.00000  0.00000  0.257061   
1  0.00000  0.00000  0.000000  ...  0.000000  0.00000  0.00000  0.000000   
2  0.00000  0.00000  0.000000  ...  0.356474  0.00000  0.00000  0.000000   
3  0.00000  0.00000  0.000000  ...  0.000000  0.27104  0.27104  0.000000   
4  0.00000  0.00000  0.000000  ...  0.000000  0.00000  0.00000  0.000000   
5  0.21782  0.21782  0.000000  ...  0.000000  0.00000  0.00000  0.000000   

      which      with      work    works    worms      you  
0  0.000000  0.000000  0.000000  0.00000  0.00000  0.00000  
1  0.293641  0.293641  0.000000  0.00000  0.00000  0.00000  
2  0.000000  0.000000  0.000000  0.00000  0.00000  0.00000  
3  0.000000  0.000000  0.000000  0.27104  0.00000  0.27104  
4  0.000000  0.000000  0.290766  0.00000  0.00000  0.00000  
5  0.000000  0.000000  0.000000  0.00000  0.21782  0.00000  

[6 rows x 71 columns]
```
