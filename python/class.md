# class

클래스 (class) : 똑같은 것을 만들어 낼 수 있는 설계 도면 (과자 틀)

객체 (object) : 클래스로 만든 피조물 (과자 틀을 사용해 만든 과자)

메소드 (method) : 클래스 내부에 정의된 함수

인스턴스 (instance) : 클래스에 의해 만들어지는 객체

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

__init__ method 는 생성자 메소드로 객체가 생성될 때 자동으로 호출됨

__del__ method 는 소멸자 메소드로 객체가 소멸될 때 자동으로 호출됨

testest 클래스는 test 클래스를 상속받아 test 기능을 그대로 사용 가능
```
