# algorithm

## 알고리즘이란

문제를 해결하기 위한 여러 동작들의 모임

## 알고리즘 조건

- 입력 : 외부에서 제공되는 자료가 0개 이상 존재
- 출력 : 적어도 2개 이상의 서로 다른 결과 필요
- 명확성 : 수행 과정은 명확하고 모호하지 않은 명령어로 구성
- 유한성(종결성) : 유한 번의 명령어를 수행 후(유한 시간 내)에 종료
- 효율성 : 모든 과정은 명백하게 실행 가능(검증 가능)한 것이어야 함

## 좋은 알고리즘이란

- 정확성 : 적당한 입력에 대해서 유한 시간내에 올바른 답을 산출하는가를 판단
- 작업량 : 전체 알고리즘에서 수행되는 가장 중요한 연산들만으로 작업량을 측정, 해결하고자 하는 문제의 중요 연산이 여러개인 경우에는 각각의 중요 연산들의 합으로 간주하거나 중요 연산들에 가중치를 두어 계산
- 기억 장소 사용량 : 수행에 필요한 저장 공간
- 최적성 : 그 알고리즘보다 더 적은 연산을 수행하는 알고리즘은 없는가? 최적이란 가장 '잘 알려진' 이 아니라 '가장 좋은'의 의미
- 시간 복잡도 : 특정 알고리즘이 어떤 문제를 해결하는데 걸리는 시간 (점근 표기법 : Big-O Notation)

### 시간 복잡도 종류 및 예시

시간 복잡도 순위

O(1) < O(logN) < O(N) < O(NlogN) < O(N<sup>2</sup>) < O(N<sup>3</sup>)

#### O(1)

입력 데이터의 수에 관계없이 일정한 실행 시간을 갖는 알고리즘

```python
arr = [1, 2, 3] # or [1, 2, 3, 4, ... 10000000]
index = 0
print(arr[0])

# arr 와 상관 없이 바로 index 를 통해 바로 데이터에 접근하므로 O(1)
```

#### O(N)

입력 데이터의 크기가 N일경우 N 번만큼의 수행시간

```python
arr = [1, 2, 3, 4, 5]
for x in arr:
    print(x)

# 반복문이 arr 길이인 5(N) 만큼 수행되므로 O(5)
```

#### O(N<sup>2</sup>)

입력 데이터의 크기가 N일경우 N<sup>2</sup> 번만큼의 수행시간

```python
n = 100
for a in range(n):
    for b in range(n):
        print(a, b)

# b for 문 N X a for 문 N 이므로 O(10000)
```

#### O(N<sup>3</sup>)

입력 데이터의 크기가 N일경우 N<sup>3</sup> 번만큼의 수행시간

```python
n = 100
for a in range(n):
    for b in range(n):
        for c in range(n):
            print(a, b, c)

# c for 문 N X b for 문 N X a for 문 N 이므로 O(1000000)
```

#### O(2<sup>n</sup>)

입력 데이터의 크기가 N일경우 2<sup>N</sup> 번만큼의 수행시간

```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1 or n == 2:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

# 재귀함수이며 return 에 2번이 들어가므로 O(2^n)
```

#### O(n!)

입력 데이터의 크기가 N일경우 n*(n-1)*(n-2)... * 1(n!) 번만큼의 수행시간

```python
def nFac(n):
    for x in range(n):
        nFac(n-1)

# nFac n x nFac n-1 ... nFac 1 이므로 O(n!)
```

#### O(logN)

입력 데이터의 크기가 N일경우 log<sub>2</sub>N 번만큼의 수행시간

```python
n = 1024
while n > 0:
    n //= 2

# n 이 절반씩 줄어들기 때문에 O(log1024)
```

#### O(NlogN)

입력 데이터의 크기가 N일경우 N*(log<sub>2</sub>N) 번만큼의 수행시간

```python
for a in range(n): # 반복횟수: n에 비례
    b = 1
    while b < n:   # 반복횟수 : log n에 비례
        print(a , b)
            b *= 2

# while 문 logn X for 문 n 이므로 O(nlogn)
```
