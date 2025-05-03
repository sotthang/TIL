# class

클래스 (class) : 똑같은 것을 만들어 낼 수 있는 설계 도면 (과자 틀)

객체 (object) : 클래스로 만든 피조물 (과자 틀을 사용해 만든 과자)

메소드 (method) : 클래스 내부에 정의된 함수

인스턴스 (instance) : 클래스에 의해 만들어지는 객체

속성 (attribute) : 클래스 내부의 메소드 또는 변수

클래스로 만든 객체는 객체마다 고유한 성격을 가짐

과자 틀로 만든 과자에 구멍을 뚫거나 조금 베어 먹더라도 다른 과자에는 아무 영향이 없는 것과 마찬가지로 동일한 클래스로 만든 객체들은 서로 전혀 영향을 주지 않음

## 클래스 선언 방법

```python
class test:    # test 는 클래스
    def __init__(self):
        pass
    def abc(self):    # abc 는 메소드
        return "abc"
    def __del__(self):
        print('delete 인스턴스')

a = test()    # a 는 객체이며 test 클래스의 인스턴스
a.abc()
>>>'abc'

class testtest(test):
    pass
```

```text
self 는 객체 a 를 자동으로 전달해줌

testest 클래스는 test 클래스를 상속받아 test 기능을 그대로 사용 가능
```

## 속성

클래스 속성과 인스턴스 속성으로 나뉨

### 클래스 속성

클래스 내부의 메소드 단계와 동일한 영역에 위치한 변수

다른 인스턴스와 데이터가 공유됨

```python
class Person:
    bag = []
 
    def put_bag(self, item):
        self.bag.append(item)
 
minji = Person()
minji.put_bag('책')
 
hani = Person()
hani.put_bag('열쇠')
 
print(minji.bag)
>>> ['책', '열쇠']
print(hani.bag)
>>> ['책', '열쇠']
```

### 인스턴스 속성

self를 통해 할당된 인스턴스만의 변수

다른 인스턴스와 데이터 공유 안됨

```python
class Person:
    def __init__(self):
        self.bag = []
 
    def put_bag(self, item):
        self.bag.append(item)
 
minji = Person()
minji.put_bag('책')
 
hani = Person()
hani.put_bag('열쇠')
 
print(minji.bag)
>>> ['책']
print(hani.bag)
>>> ['열쇠']
```

## 메소드 종류

### 인스턴스 메소드

클래스에서 데코레이터 없이 선언

첫번째 매개 변수로 클래스의 인스턴스가 넘어오는데 관행적으로 self 를 사용

self 를 통해 인스턴스 속성(attribute)에 접근하거나 다른 인스턴스 메소드를 호출 가능, 클래스 속성에 접근하거나 클래스 메소드를 호출 가능

### 클래스 메소드

@classmethod 로 선언

첫번째 매개 변수로 클래스 인스턴스가 아닌 클래스 자체가 넘어오는데 관행적으로 cls 를 사용

cls 를 통해 클래스 속성(attribute)에 접근하거나, 클래스 메소드를 호출 가능

인스턴스 메소드와 달리 인스턴스 속성에 접근하거나 다른 인스턴스 메소드를 호출하는 것은 불가능

### 정적 메소드

@staticmethod 로 선언

첫번째 매개 변수가 할당되지 않음

정적 메소드 내에서는 인스턴스 및 클래스 속성에 접근하거나, 인스턴스 및 클래스 메소드를 호출하는 것이 불가능
