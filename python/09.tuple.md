# 튜플

불변하는 숫자, 문자 등이 나열되어 있는 집합 (tuple)

리스트는 [] 로 되어있으나 튜플은()

## 튜플형 선언 방법 및 불변 확인

```python
a = (1, 'a', (2, 'b'))
a
>>> (1, 'a', (2, 'b'))
del a[0]
>>> Traceback (most recent call last):
>>>   File "<stdin>", line 1, in <module>
>>> TypeError: 'tuple' object doesn't support item deletion
a[1] = 2
>>> Traceback (most recent call last):
>>>   File "<stdin>", line 1, in <module>
>>> TypeError: 'tuple' object does not support item assignment
```

## 튜플형 인덱싱 (indexing)

```python
a = (1, 'a', (2, 'b'))
a[2]
>>> (2, 'b')
```

## 튜플형 슬라이싱 (Slicing)

```python
a = (1, 'a', (2, 'b'))
a[1:]
>>> ('a', (2, 'b'))
```

## 튜플형 덧셈, 곱셈

```python
a = (1, 3, 5)
b = (2, 4, 6)
a+b
>>> (1, 3, 5, 2, 4, 6)
a*3
>>> (1, 3, 5, 1, 3, 5, 1, 3, 5)
```

## 튜플형 길이 계산

```python
a = (1, 2, 3, 4, 5, 6, 7, 8, 9)
len(a)
>>> 9
```
