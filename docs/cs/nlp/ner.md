# Named Entity Recognition

## NER 이란

단어 또는 구가 사람, 장소, 조직 같은 특정 개체인지 태그하는 것

```python
import spacy

nlp = spacy.load("en_core_web_sm")

text = "Apple was founded by Steve Jobs in California."
doc = nlp(text)

for ent in doc.ents:
    print((ent.text, ent.label_))
```

```output
('Apple', 'ORG')
('Steve Jobs', 'PERSON')
('California', 'GPE')
```
