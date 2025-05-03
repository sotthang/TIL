# heap

## heap 이란

우선 순위 큐를 위해 만들어진 자료구조로 최댓값 또는 최솟값을 찾는 연산에 특화됨

우선 순위 큐 : 우선 순위가 높은 데이터가 먼저 out 되는 자료 구조

ex) 네트워크 트래픽 제어, 작업 스케줄링 등

## heap 종류

### max heap

부모 노드가 자식 노드보다 값이 크거나 같은 이진 트리

### min heap

부모 노드가 자식 노드보다 값이 작거나 같은 이진 트리

## heapq

파이썬 모듈로 리스트를 min heap 처럼 사용 가능

```python
import heapq

heap = []
heapq.heappush(heap, 1)    # 노드 추가
print(heap)
>>> [1]

heapq.heappop(heap)    # 노드 삭제
print(heap)
>>> []

heapq.heappush(heap, (2, 'b'))    # (리스트, (우선 순위, 값))
heapq.heappush(heap, (1, 'a'))
print(heap)
>>> [(1, 'a'), (2, 'b')]    # 우선 순위 (오름차순) 로 정렬됨

heap2 = [7, 5, 8, 3]
heapq.heapify(heap2)    # 리스트를 heap 으로 변경
print(heap2)
>>> [3, 5, 8, 7]
```

우선 순위를 사용하여 max heap 구현

```python
import heapq

number = [3, 7, 4, 1, 9, 5]
heap = []
for num in number:
  heapq.heappush(heap, (-num, num))
print(heap)
>>> [(-9, 9), (-7, 7), (-5, 5), (-1, 1), (-3, 3), (-4, 4)]

for _ in range(len(heap)):
  print(heapq.heappop(heap)[1])
>>> 9
    7
    5
    4
    3
    1
```
