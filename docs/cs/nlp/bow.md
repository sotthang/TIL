# Bag of Words

## Bag of Words (BoW) 란

 NLP에서 가장 기본적이고 직관적인 텍스트 벡터화 방법 중 하나
 
 문장에서 단어의 순서를 무시하고 어떤 단어들이 등장했는지만 고려해 벡터화

```python
import pandas as pd
from sklearn.feature_extraction.text import CountVectorizer

data = [' Most shark attacks occur about 10 feet from the beach since that is where the people are',
        'the efficiency with which he paired the socks in the drawer was quite admirable',
        'carol drank the blood as if she were a vampire',
        'giving directions that the mountains are to the west only works when you can see them',
        'the sign said there was road work ahead so he decided to speed up',
        'the gruff old man sat in the back of the bait shop grumbling to himself as he scooped out a handful of worms']
countvec = CountVectorizer()
countvec_fit = countvec.fit_transform(data)
bag_of_words = pd.DataFrame(countvec_fit.toarray(), columns = countvec.get_feature_names_out())

print(bag_of_words)
```

```output
   10  about  admirable  ahead  are  as  attacks  back  bait  beach  ...  \
0   1      1      0      0       1    0     1      0     0      1    ...   
1   0      0      1      0       0    0     0      0     0      0    ...   
2   0      0      0      0       0    1     0      0     0      0    ...   
3   0      0      0      0       1    0     0      0     0      0    ...   
4   0      0      0      1       0    0     0      0     0      0    ...   
5   0      0      0      0       0    1     0      1     1      0    ...   

   were  west  when  where  which  with  work  works  worms  you  
0    0     0     0      1      0     0     0      0      0    0  
1    0     0     0      0      1     1     0      0      0    0  
2    1     0     0      0      0     0     0      0      0    0  
3    0     1     1      0      0     0     0      1      0    1  
4    0     0     0      0      0     0     1      0      0    0  
5    0     0     0      0      0     0     0      0      1    0  

[6 rows x 71 columns]
```

