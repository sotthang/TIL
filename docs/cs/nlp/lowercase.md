# Lowercase (소문자)

## NLP 에서의 Lowercase

텍스트 데이터에서 중요한 첫 단계는 소문자로 변환하는 것

데이터와 출력 결과의 일관성을 유지하는데 도움이 되고, 대소문자를 구분할 필요가 없어지므로 추가 데이터 정리가 쉬움

하지만 소문자로 변환하면 일부 텍스트의 의미가 달라질 수 있음 (ex: "US" 는 국가로 인식)

```python
sentence = "Her cat's name is Naru"
lower_sentence = sentence.lower()

print(lower_sentence)
```

```output
her cat's name is naru
```

```python

sentence_list = ['Could you pass me the TV remote?', 
                 'It is IMPOSSIBLE to find this hotel', 
                 'Want to go for dinner on Tuesday?']
lower_sentence_list = [x.lower() for x in sentence_list]

print(lower_sentence_list)
```

```output
['could you pass me the tv remote?', 'it is impossible to find this hotel', 'want to go for dinner on tuesday?']
```
