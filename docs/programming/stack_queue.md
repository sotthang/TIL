# stack and queue

## 스택 이란

가장 먼저 들어 온 개체가 가장 마지막에 나가는 (Last in first out, LIFO) 방식을 사용하는 자료구조, (ex: 프링글스 통)

파이썬에서는 리스트 사용

```python
stack = []

stack.append(1)
stack.append(2)
stack.append(3)

print(stack.pop())
>>> 3
print(stack.pop())
>>> 2
print(stack.pop())
>>> 1
```

## 큐 란

가장 먼저 들어온 개체가 가장 먼저 나가는 (First in first out, FIFO) 방식을 사용하는 자료구조, (ex: 택시정거장)

- enqueue : 큐에 데이터 입력
- dequeue : 큐에서 데이터 출력

파이썬에서는 queue 라는 내장함수 사용

```python
import queue

queue_data = queue.Queue()
print(type(queue_data))

>>> <class 'queue.Queue'>

queue_data.put(1)
queue_data.put(2)
queue_data.put(3)

print(queue_data.get())
>>> 1
print(queue_data.get())
>>> 2
print(queue_data.get())
>>> 3
```