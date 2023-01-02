# 리스트
리스트형의 정의 : 숫자, 문자 등이 나열되어 있는 집합 (list)
<br>
변경 가능 (mutable), 반복 가능 (iterable)
<br>

## 리스트 선언 방법
대괄호 []
```python
a = ['a', 1, ['z', 'x', 'y']]
 ```

## 리스트 인덱싱 (indexing)
```python
a = ['a', 1, ['z', 'x', 'y']]

a[0]
'a'

a[2][1]
'x'
```
<br>

## 리스트 슬라이싱 (Slicing)
```python
a = ['a', 1, ['z', 'x', 'y']]

a[0:2]
['a', 1]

a[2][:2]
['z', 'x']
```
<br>

## 리스트 덧셈, 곱셈
```python
a = [1, 3, 5]
b = [2, 4, 6]

a+b
[1, 3, 5, 2, 4, 6]

a*2
[1, 3, 5, 1, 3, 5]
```
<br>

## 리스트 길이 계산
```python
a = [1, 3, 5, 7, 9]
len(a)
5
```
<br>

## 리스트 값 변경, 삭제
```python
a = [1, 3, 5, 7, 9]
a[2] = 6

a
[1, 3, 6, 7, 9]
del a[2]


a
[1, 3, 7, 9]
del a[2:]
a
[1, 3]
```
<br>

## 리스트 내장함수

### append : 리스트에 값 추가
```python
a = [1, 3, 5]
a.append(7)
a.append([9, 11])

a
[1, 3, 5, 7, [9, 11]]
```
<br>

### sort : 오름차순 정렬
```python
a = [4, 1, 8, 6, 2]
a.sort()
a
[1, 2, 4, 6, 8]
```
<br>

### reverse : 역순으로 정렬
```python
a = [1, 3, 6]
a.reverse()
a
[6, 3, 1]
```
<br>

### index : 처음 나오는 위치 (없다면 오류 발생)
```python
a = [1, 3, 5, 3, 7]
a.index(3)
1
a.index(2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 2 is not in list
```
<br>

### insert : 특정 위치에 값 추가
```python
a = [1, 3, 4, 5]
a.insert(1, 2)
a
[1, 2, 3, 4, 5]
```
<br>

### remove : 처음 나오는 값 제거 (없다면 오류 발생)
```python
a = [1, 3, 5, 3, 7]
a.remove(3)
a
[1, 5, 3, 7]
a.remove(9)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list
```
<br>

### pop : 리스트의 마지막 값을 반환하고 삭제 <br>pop(x) : x번째 값을 반환하고 삭제
```python
a = [1, 3, 5, 3, 7]
a.pop()
7
a
[1, 3, 5, 3]
a.pop(2)
5
a
[1, 3, 3]
```
<br>

### count : 문자 갯수 세기
```python
a = [1, 3, 5, 3, 5, 3, 1]
a.count(3)
3
```
<br>

### extend : 리스트에 리스트형 추가
```python
a = [1, 3, 5]
a.extend([7, 9])
a
[1, 3, 5, 7, 9]
```
<br>
