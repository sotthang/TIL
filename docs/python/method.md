# method

## 메소드란

함수처럼 특정 기능을 수행하지만 함수와는 다르게 클래스 및 객체와 연관되어 있음

```python
a = 'abc'
a.upper()
>>> 'ABC'

# .upper() 가 메소드
```

## magic method

파이썬에서 특별하게 사용되는 메소드

### magic method list

```text

__init__ : 생성자 메소드로 인스턴스 객체가 생성되면 호출

__del__ : 소멸자 메소드로 인스턴스 객체가 소멸(파괴) 될 때 호출

__iter__ : iterabl 한 객체를 만들때 사용

__next__ : iterator 를 만들때 사용

__add__ : + 연산 호출

__sub__ : - 연산 호출

__mul__ : * 연산 호출

__truediv__ : / 연산 호출
```

```text
비교 매직 메소드

__lt__ : x < y 를 판단하는 기준을 정의 (less than → lt)

__le__ : x ≤ y 를 판단하는 기준을 정의 (less than or equal to → le)

__gt__ : x > y 를 판단하는 기준을 정의 (greater than → gt)

__ge__ : x ≥ y 를 판단하는 기준을 정의 (greater than or equal to → ge)

__eq__ : x == y 를 판단하는 기준을 정의 (equal to → eq)

__ne__ : x != y 를 판단하는 기준을 정의 (not equal to → ne)
```
