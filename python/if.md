# if

조건에 해당하는 코드를 실행시키기 위해 사용

## if 문의 구조

```python
if 조건:
    코드
    코드
else:
    코드
    코드

if 조건:
    코드
    코드
elif 조건:
    코드
    코드
elif 조건:
    코드
    if 조건:
        코드
else:
    코드
    코드
```

```python
a = 1
if a == 1:
    print('a 는 1 입니다.')
else:
    print('a 는 1 이 아닙니다.')

>>> 'a는 1 입니다.'
```

if 만 있어도 사용 가능, else 는 if 가 있어야 사용 가능

조건은 True 또는 False 처럼 참 혹은 거짓을 판단 할 수 있어야 함

조건문 안에 다른 조건문을 중첩으로 사용 가능

## 비교연산자

```python
a = 5
if a > 3:
    print('a 는 3 보다 큽니다.')
else:
    print('a 는 3 보다 작습니다.')

>>> 'a 는 3 보다 큽니다.'

b = 1
if b > 3:
    print('b 는 3 보다 큽니다.')
else:
    print('b 는 3 보다 작습니다.')

>>> 'b 는 3 보다 작습니다.'
```

## 조건 연산자

```python
a = 5
if a > 3 and a < 7:
  print('a 는 3 보다 크고 7 보다 작습니다.')
else:
  print('a 는 3 보다 작거나 7 보다 큽니다.')

>>> 'a 는 3 보다 크고 7 보다 작습니다.'

list = [1, 3, 5]
if 3 in list:
  print('리스트 안에 있습니다.')
elif 4 not in list:
  print('4 는 리스트 안에 없습니다.')
else:
  print('리스트 안에 없습니다.')

>>> '리스트 안에 있습니다.'

tuple = (2, 6, 8)
if 3 in tuple:
  print('튜플 안에 있습니다.')
elif 4 not in tuple:
  print('4 는 튜플 안에 없습니다.')
else:
  print('튜플 안에 없습니다.')

>>> '4 는 안에 없습니다.'
```

## 조건부 표현식

한줄로 간단하게 코딩 가능

```python
a = 1000
if a > 500:
    b = a
else:
    b = 0

# 위와 아래 코드는 같은 코드

a = 1000
b = a if a > 500 else 0
```
