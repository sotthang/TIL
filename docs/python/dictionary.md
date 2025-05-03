# 딕셔너리

낱말, 단어 등의 의미가 정의되어 있는 사전처럼 Key 와 Value 로 이루어진 집합 (Dictionary)

## 딕셔너리형 선언 방법

```python
a = {'name':'apple', 'age':'3', 'num':'1221'}
a
>>> {'name': 'apple', 'age': '3', 'num': '1221'}

b = {1:'abc'}
b[2] = '123'
b
>>> {1: 'abc', 2: '123'}
```

## 딕셔너리형 값 삭제

```python
a = {'name':'apple', 'age':'3', 'num':'1221'}
del a['num']
a
>>> {'name': 'apple', 'age': '3'}
```

## Key 를 사용하여 Value 값 얻기

```python
a = {'name':'apple', 'age':'3', 'num':'1221'}
a['name']
>>> 'apple'
```

## 딕셔너리형 주의사항

Key 값이 중복될 경우 마지막 Key 값만 선언됨  
Key 값에는 리스트형을 사용할 수 없음

## 딕셔너리 함수

### keys() : key 값 전부 출력

### values() : value 값 전부 출력

```python
test = {'a':1, 'b':2, 'c':3}
test.keys()
>>> dict_keys(['a', 'b', 'c'])
test.values()
>>> dict_values([1, 2, 3])
```

### items() : key 와 value 를 튜플형으로 출력

```python
test = {'a':1, 'b':2, 'c':3}
test.items()
>>> dict_items([('a', 1), ('b', 2), ('c', 3)])
```

### clear() : key 와 value 모두 삭제

```python
test = {'a':1, 'b':2, 'c':3}
test.clear()
test
>>> {}
```

### get() : key 값으로 value 값 얻기

a.get('key') 에서 key 가 없다면 None 값을 리턴  
key 가 없더라도 특정 값을 리턴받고 싶다면 a.get('key', 'value') 사용  
a['key'] 에서 key 가 없다면 error 발생  

```python
test = {'a':1, 'b':2, 'c':3}
test.get('a')
>>> 1
test.get('d')
test['d']
>>> Traceback (most recent call last):
>>>   File "<stdin>", line 1, in <module>
>>> KeyError: 'd'
test.get('d', '4')
>>> '4'
```

### in : 딕셔너리형에 key 값이 존재하는지 확인

```python
test = {'a':1, 'b':2, 'c':3}
'a' in test
>>> True
'd' in test
>>> False
```
