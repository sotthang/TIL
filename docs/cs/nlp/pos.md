# Parts of Speech (POS) Tagging

## POS 란

단어마다 품사(명사, 동사, 형용사 등)을 붙이는 것

```python
import nltk
nltk.download("punkt")
nltk.download("averaged_perceptron_tagger")

text = "I love Python programming."
tokens = nltk.word_tokenize(text)
tagged = nltk.pos_tag(tokens)

print(tagged)
```

```output
[('I', 'PRP'), ('love', 'VBP'), ('Python', 'NNP'), ('programming', 'NN')]
```
