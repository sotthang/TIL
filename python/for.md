# for

iterable 객체를 순회하며 코드 실행

## for 문의 구조

```python
for 변수 in iterable:
    코드
    코드

for 변수 in iterable:
    코드
    코드
    if 조건:
        break
else:
    코드

# for 문에서 break 가 실행 되면 else 코드는 실행 안됨
# break 가 실행 안되면 else 코드 실행됨
```

## for 문 iterable

for 문에서 사용되는 iterable 종류

### string

```python
for x in "python":
    print(x)

>>> p
>>> y
>>> t
>>> h
>>> o
>>> n
```

### list

```python
a = [1, 2, 3]
for x in a:
    print(x)

>>> 1
>>> 2
>>> 3

b = [[1, 2], [3, 4], [5, 6]]
for x, y in b:
    print(x + y)

>>> 3
>>> 7
>>> 11
```

### range

```python
for x in range(0, 5):
    print(x)

>>> 0
>>> 1
>>> 2
>>> 3
>>> 4
```

## 리스트 내포의 구조

[표현식 for 변수 in 반복가능객체]

or

[표현식 for 항목 in 반복가능객체 if 조건문]

```python
d = [2, 4, 6]
e = [x * 3 for x in d]
print(e)

>>> [6, 12, 18]
```
