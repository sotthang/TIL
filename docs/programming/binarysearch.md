# 이진탐색

## 이진탐색 이란

범위를 절반씩 좁혀가며 탐색해가는 알고리즘

탐색해야 할 데이터가 많을 때 사용하며 정렬되있을때만 사용 가능

시간복잡도는 O(log N)

### while 문으로 구현

```python
binary_list = [i for i in range(1, 101)]
start = 0
end = len(binary_list)
target = 26
while start < end:    # target 의 index 값을 탐색
    print(start, end)
    mid = (start + end) // 2
    if binary_list[mid] < target:
        start = mid + 1
    else:
        end = mid
print(binary_list[start])

>>> 0 100
    0 50
    0 25
    13 25
    20 25
    23 25
    26
```

### 재귀함수로 구현

```python
def binary_search(arr, target, start, end):
    mid = (start + end) // 2
    print(start, end)
    if arr[mid] == target:
        return mid
    elif arr[mid] > target:
        return binary_search(arr, target, start, mid-1)
    else:
        return binary_search(arr, target, mid+1, end)

binary_list = [i for i in range(1, 101)]
start = 0
end = len(binary_list)
target = 26
print(binary_list[binary_search(binary_list, target, start, end)])
```