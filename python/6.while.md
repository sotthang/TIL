# while

코드를 반복해서 실행 할 때 사용 (잘못하면 무한 반복이 되기에 빠져나갈 수 있는 조건이나 break 필요)

## while 문의 구조

```python
while 조건:
    코드
    코드
```

```python
a = 0
while a < 5:
    print(a)
    a += 1

>>> 0
>>> 1
>>> 2
>>> 3
>>> 4
>>> 5
```

## 반복문 제어

for 문, while 문 제어 시 사용

### pass

아무 처리도 되지 않음 (조건문 동작 확인 등에 사용)

```python
for x in range(5):
    if x == 3:
        pass
    print(x)

>>> 0
>>> 1
>>> 2
>>> 3
>>> 4

# x == 3 일 때 pass 되어 print(x) 가 실행되어 3이 출력됨
```

### break

반복문에서 루프를 빠져나옴 (이중 반복일 때는 해당 루프만 빠져나옴)

```python
for x in range(5):
    if x == 3:
        break
    print(x)

>>> 0
>>> 1
>>> 2

# x == 3 일 때 break 되어 반복문이 더이상 동작하지 않아 print(x) 는 실행되지 않음
```

### continue

다음 루프로 넘어감

```python
for x in range(5):
    if x == 3:
        continue
    print(x)

>>> 0
>>> 1
>>> 2
>>> 4

# x == 3 일 때 continue 되어 print(x) 는 실행되지 않고 다음 루프인 x == 4 로 넘어감
```
