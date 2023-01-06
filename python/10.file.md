# file

## 파일 열기

open(파일명, 모드, 인코딩)

|Character|Meaning|
|---------|-------|
|'r'|open for reading (default)|
|'w'|open for writing, truncating the file first|
|'x'|open for exclusive creation, failing if the file already exists|
|'a'|open for writing, appending to the end of file if it exists|
|'b'|binary mode|
|'t'|text mode (default)|
|'+'|open for updating (reading and writing)|

```text
# python.txt
py
thon
```

```python
f = open('python.txt', mode='r', encoding=None)
print(f)
>>> <_io.TextIOWrapper name='python.txt' mode='r' encoding='UTF-8'>

print(f.read())
>>> py
>>> thon

f.close()

# open 했으면 close 해야 데이터 유실 없음
```

or

```python
with open('python.txt') as f:
    print(f.read())
>>> py
>>> thon

# with 는 close 필요 없어서 자주 사용
```

## 파일 쓰기

write

```text
# python.txt
py
thon
```

```python
with open('python.txt', 'a') as f:
    f.write('hello')
```

```text
# python.txt
py
thonhello
```

```python
with open('python.txt', 'w') as f:
    f.write('what')

# write 는 문자열로 입력
```

```text
# python.txt
what
```

```python
with open('python.txt', 'w') as f:
    f.writeline(['abc', 'def\n', 'gh'])

# writelines 는 리스트, 튜플 같은 문자열 컬렉션으로 입력
```

```text
# python.txt
abcdef
gh
```

## 파일 읽기

read

```text
# python.txt
py
thon
```

```python
with open('python.txt', 'r') as f:
    while True:
        x = f.read()
        if x == '':    # while 문 탈출이 필요하기에 x 가 빈 문자열이면 break
            break
        print(x)
>>> py
>>> thon

# read 는 한 글자씩 읽어오며 더이상 읽을 내용 없으면 종료
```

```python
with open('python.txt', 'r') as f:
    while True:
        x = f.readline()
        if x == '':
            break
        print(x)
>>> py
>>> 
>>> thon

# readline 은 한 줄씩 읽어오며 더이상 읽을 내용 없으면 종료
```

```python
with open('python.txt', 'r') as f:
    print(f.readlines())
>>> ['py\n', 'thon']

# readlines 은 한 줄씩 리스트로 저장
```
