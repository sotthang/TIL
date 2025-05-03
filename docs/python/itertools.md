# itertools

## itertools 란

파이썬 내장 라이브러리로 효율적인 루핑을 위한 이터레이터를 만드는 함수

### itertools 대표 함수

- count : 숫자 start로 시작하여 균등 간격의 값을 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.count(10):
    print(x)

>>> 10
    11
    12
    13
    14
    15
    ...
```

```python
import itertools

for x in itertools.count(10, 5):
    print(x)

>>> 10
    15
    20
    25
    30
    35
    ...
```

- cycle : 정해져있는 요소를 반복적으로 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.cycle([1, 2, 3]):
    print(x)

>>> 1
    2
    3
    1
    2
    3
    1
    2
    3
    ...
```

-  repeat : 특정 요소를 무한히 혹은 특정 횟수 만큼 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.repeat(2):
    print(x)

>>> 2
    2
    2
    2
    2
    2
    ...
```

```python
import itertools

for x in itertools.repeat(5, 3):
    print(x)

>>> 5
    5
    5
```

- accmulate : 요소들의 누적 합을 반환하는 이터레이터 생성

```python
import itertools

data=[1,2,3,4,5,6,7,8,9,10]

print(*itertools.accumulate(data))

>>> 1 3 6 10 15 21 28 36 45 55
```

- compress : 1인 요소들만 반환하는 이터레이터 생성

```python
import itertools

data=[1,0,1,1,0,1]

print(*itertools.compress('abcdef', data))

>>> a c d f
```

- product : 데카르트의 곱 (각각의 값들을 순서쌍으로 이루어진 집합으로 만들기 위한 연산) 을 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.product('abcd', repeat=2):
    print(x)

>>> ('a', 'a')
    ('a', 'b')
    ('a', 'c')
    ('a', 'd')
    ('b', 'a')
    ('b', 'b')
    ('b', 'c')
    ('b', 'd')
    ('c', 'a')
    ('c', 'b')
    ('c', 'c')
    ('c', 'd')
    ('d', 'a')
    ('d', 'b')
    ('d', 'c')
    ('d', 'd')
```

- permutations : 요소들의 중복 및 순서 상관없이 모든 경우의 수를 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.permutations('abcd', 2):
    print(x)

>>> ('a', 'b')
    ('a', 'c')
    ('a', 'd')
    ('b', 'a')
    ('b', 'c')
    ('b', 'd')
    ('c', 'a')
    ('c', 'b')
    ('c', 'd')
    ('d', 'a')
    ('d', 'b')
    ('d', 'c')
```

- combinations : 요소들의 중복은 없으나 순서를 따지는 경우의 수를 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.combinations('abcd', 2):
    print(x)

>>> ('a', 'b')
    ('a', 'c')
    ('a', 'd')
    ('b', 'c')
    ('b', 'd')
    ('c', 'd')
```

- combinations_with_replacement : 요소들의 중복을 허용하고 순서가 정렬된 경우의 수를 반환하는 이터레이터 생성

```python
import itertools

for x in itertools.combinations_with_replacement('abcd', 2):
    print(x)

>>> ('a', 'a')
    ('a', 'b')
    ('a', 'c')
    ('a', 'd')
    ('b', 'b')
    ('b', 'c')
    ('b', 'd')
    ('c', 'c')
    ('c', 'd')
    ('d', 'd')
```
