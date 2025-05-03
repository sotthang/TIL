# namespace

파이썬에서 변수명을 객체에 연결해주는 영역이며 4개의 scope 로 나뉨

## scope

파이썬에서 변수를 확인할 때 LEGB 순서대로 확인

(Local 에 변수가 없는 경우 Enclosed 에서 확인  
Enclosed 에도 변수가 없다면 Global, Global 에도 없다면 Built-in 에서 확인)

### local

함수, 클래스 의 namespace

### enclosed

함수 내에 함수가 있는 경우 상위 함수의 namespace

### global

함수 밖의 namespace

### built-in

파이썬에서 사용되는 예약어

## Variable Shadowing

동일한 이름의 변수를 LEGB 중 두 군데 이상에서 사용하는 경우

```python
var = 'a'

def inout():
    var = 'b'
```
