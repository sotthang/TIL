# Early Return

## 얼리 리턴이란?

함수가 실행되는 도중에 조건을 만족하면 함수의 실행을 즉시 종료하고 값을 반환하는 프로그래밍 패턴

이는 함수의 중간에 있는 코드 블록에서 조건을 확인하여 더 이상의 계산이나 처리를 할 필요가 없을 때 유용하게 사용

얼리 리턴 적용 전

```python
def find_smallest_positive_number(numbers):
    smallest = None
    for n in numbers:
        if n > 0:
            if smallest is None or n < smallest:
                smallest = n
    return smallest

print(find_smallest_positive_number([3, 6, -2, -6, -8, 1, 4, 6]))

>> 1
```

얼리 리턴 적용 후

```python
def find_smallest_positive_number(numbers):
    smallest = None
    for n in numbers:
        if n == 1:
            return 1
        elif n > 0:
            if smallest is None or n < smallest:
                smallest = n
    return smallest

print(find_smallest_positive_number([3, 6, -2, -6, -8, 1, 4, 6]))

>> 1
```

적용 전 코드는 모든 요소가 for 문으로 실행되지만 적용 후 코드는 최소 양수인 1 이 있으면 이후 요소는 확인 할 필요 없이 바로 리턴 한다.

모든 상황에 적용되는 프로그래밍 패턴은 아니기에 상황에 맞춰 사용하면 효율적이고 가독성 좋은 코드가 될 수 있다.
