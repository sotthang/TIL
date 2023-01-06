# 모듈

## 라이브러리 vs 패키지 vs 모듈

모듈 : 변수, 함수 또는 클래스를 코딩해놓은 것

패키지 : 특정 기능과 관련된 여러 모듈을 모아놓은 것

라이브러리 : 여러 패키지와 모듈을 모아놓을 것

import module name 으로 추가 가능

```python
import math
math.fabs(-12.34)
>>> 12.34
 ```

직접 파일을 만들어서 사용 할 수 있음

```python
# moduletest.py
def add(a, b):
    return a+b

def sub(a, b):
    return a-b
```

```python
# moduletest.py 와 같은 폴더에서 실행
import moduletest
print(moduletest.add(7, 3))
>>> 10
print(moduletest.sub(7, 3))
>>>4
```

module 이름 없이 사용하고 싶다면 from module name import module def 로 사용 가능

```python
from moduletest import add
add(7, 3)
>>> 10
```

module 의 모든 함수를 이름 없이 사용 하고 싶다면 import * 로 사용 가능

```python
>>> from moduletest import *
>>> add(7, 3)
10
>>> sub(7, 3)
4
```

```text
module 코드 중 if __name__ ==  "__main__" 은 module 파일을 직접 실행했을 때는 조건이 참이 되어 if 문 아래가 실행되나 대화형 인터프리터나 다른 파일에서 module 을 사용하면 조건이 거짓이 되어 실행 안됨

__name__ : 파이썬에서 내부적으로 사용하는 특별한 변수

위 케이스 중 대화형 인터프리터나 다른 파일에서 module 을 사용하면 __name__ 은 module 이름이 저장된다
```
