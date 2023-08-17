# PDB 

## PDB 란

PDB 모듈은 파이썬 프로그램을 위한 대화형 소스 코드 디버거를 정의

## 사용 방법

import pdb; pdb.set_trace() 또는 breakpoint() 로 사용

```python
def double(x):
   breakpoint()
   return x * 2
val = 3
print(f"{val} * 2 is {double(val)}")

>>> ...(3)double()
>>> -> return x * 2
>>> (Pdb) p x
>>> 3
>>> (Pdb) continue
>>> 3 * 2 is 6
```

명령어
- s(tep) : 현재 줄을 실행하고, 멈출 수 있는 가장 첫 번째 줄(호출되는 함수 또는 현재 함수의 다음 줄) 에서 멈춤
- n(ext) : 현재 함수의 다음 줄에 도달하거나, 반환할 때까지 계속 실행, next와 step의 차이점은 step은 호출된 함수 안에서 멈추고, next는 호출된 함수를 재빠르게 실행하고 현재 함수의 바로 다음 줄에서만 멈춤
- r(eturn) : 현재 함수가 반환될 때까지 계속 실행
- c(ont(inue)) : 중단점을 마주칠 때까지 계속 실행
