# 문자열

문자, 단어 등으로 이루어진 문자들의 집합 (string)

변경 불가능 (immutable), 반복 가능 (iterable)

## 문자열 선언 방법

1. 큰 따옴표(")
2. 작은 따옴표(')
3. 큰 따옴표 3개 (""")
4. 작은 따옴표 3개(""")

```python
a = "Hello World"
b = '12345'
c = """aeiou"""
d = '''sotthang'''
 ```

## 문자열 안에 따옴표를 넣고 싶을 때

```python
a = """sotthang's python"""
b = '''"Hello World"'''
c = 'sotthang\'s Python'
 ```

## 두 줄 이상의 문자형 선언하는 방법

```python
a = 'sotthang\nblog'
b = """
... sotthang 
... python
... """
```

## 문자열 연산

```python
a = 'sotthang'
b = 'python'

a + b
>>> 'sotthangpython'

a * 2
>>> 'sotthangsotthang'
 ```

## 문자열 길이 계산

```python
a = 'sotthang'

len(a)
>>> 8
```

## 문자열 인덱싱 (indexing)

첫 문자부터 순서대로 0, 1, 2, 3 ... 숫자를 매김

숫자 앞에 - 가 붙는다면 맨 뒤 문자부터 -1, -2, -3 ... 숫자를 매김

```python
a = 'sotthangblog'

a[0]
>>> 's'

a[8]
>>> 'b'

a[11]
>>> 'g'

a[12]
Traceback (most recent call last):
  File "<stdin>", ling 1, in <module>
IndexError : string index out of range

a[-1]
>>> 'g'
a[-2]
>>> 'o'
a[-12]
>>> 's'
```

## 문자열 슬라이싱 (Slicing)

슬라이싱 한 range 의 문자들을 선언

a[0:8] : 0부터 7까지의 문자들을 슬라이싱

```python
a = 'sotthang python blog'

a[0:8]
>>> 'sotthang'

a[9:17]
>>> 'python b'

a[12:]
>>> 'hon blog'

a[:11]
>>> 'sotthang py'
```

## 문자열 포맷팅 (Formatting)

원하는 위치에 특정 값을 입력

(ex: I **** python,
**** = love or like or hate ...)

## string 입력

```python
'I %s python.' % 'love'
>>> 'I love python.'

'I %s python.' % 'like'
>>> 'I like python.'

'I %s python.' % 'hate'
>>> 'I hate python.'
 ```

## number 입력

```python
'I have %d apples.' % 3
>>> 'I have 3 apples'

'I have %d apples.' % 4
>>> 'I have 4 apples'
 ```

## 변수 입력

```python
number = 5
'I have %d apples.' % number
>>> 'I have 5 apples.'

day = 'today'
'I ate %d apples %s' % (number, day)
>>> 'I ate 5 apples today'
```

## 이스케이프 코드

프로그래밍에서 사용할 수 있도록 정의해 둔 코드

```text
\n : 줄바꿈
\t : 탭 입력
\\ : \ 사용
\' : 작은 따옴표 사용
\" : 큰 따옴표 사용
%s : 문자형
%c : 문자 1개
%d : 정수
%f : 부동소수
%% : 문자%
```

이스케이프 코드 무시 방법 : 앞에 r 을 입력 (raw string)

```python
print(r'\\ \n')
>>> \\ \n
```

## 정렬 및 공백

```python
'%10s' % 'python'
>>> '    python'

'%-10s' % 'python'
>>> 'python    '
```

"%10s" % "python" = 총 문자형 10개 중 python 을 제외한 4개의 공백을 왼쪽으로 정렬

"%-10s" % "python" = 총 문자형 10개 중 python 을 제외한 4개의 공백을 오른쪽으로 정렬

## 소수점

```python
'%0.3f' % 0.123456789
>>> '0.123'

'%0.5f' % 0.123456789
>>> '0.12346'

'%0.7f' % 0.123456789
>>> '0.1234568'
```

## format 함수 사용

```python
'I have {0} apples.'.format(2)
>>> 'I have 2 apples.'

'I have {0} apples.'.format('three')
>>> 'I have three apples.'

number = 4
'I have {0} apples.'.format(number)
>>> 'I have 4 apples.'

day = 'today'
'I ate {0} apples {1}'.format(number, day)
>>> 'I ate 4 apples today'

'I ate {number} apples {day}'.format(number=5, day='today')
>>> 'I ate 5 apples today'

'{0:<10}'.format('python')
>>> 'python    '
'{0:>10}'.format('python')
>>> '    python'
'{0:^10}'.format('python')
>>> '  python  '

a = 0.123456789
'{0:0.3f}'.format(a)
>>> '0.123'
'{0:0.5f}'.format(a)
>>> '0.12346'
 ```

## f 문자형 포맷팅

```python
number = 2
day = 'today'
f'I ate {number} apples {day}.'
>>> 'I ate 2 apples today.'
f'I ate {number+5} apples {day}.'
>>> 'I ate 7 apples today.'

a = {'number':3, 'day':'today'}
f'I ate {a["number"]} apples {a["day"]}.'
>>> 'I ate 3 apples today.'

f'{"python":<10}'
>>> 'python    '
f'{"python":>10}'
>>> '    python'
f'{"python":^10}'
>>> '  python  '

b = 0.123456789
f'{b:0.3f}'
>>> '0.123'
f'{b:0.5f}'
>>> '0.12346'
```

## 문자형 내장 함수

### count : 문자 갯수 세기

```python
a = "happy"

a.count('p')
>>> 2
```

### find : 처음 나오는 문자 위치 (없다면 -1 을 return)

```python
a = "I love python."

a.find('o')
>>> 3
a.find('a')
>>> -1
```

### index : 처음 나오는 문자 위치 (없다면 오류 발생)

```python
a = "I love python."

a.index('o')
>>> 3
a.index('a')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: substring not found
```

### join : 문자형 삽입

```python
":".join('123456789')
>>> '1:2:3:4:5:6:7:8:9'
":".join(['1','2','3','4','5','6','7','8','9'])
>>> '1:2:3:4:5:6:7:8:9'
```

### upper : 소문자를 대문자로 변경 lower : 대문자를 소문자로 변경

```python
a = "python"

a.upper()
>>> 'PYTHON'

b = "PYTHON"

b.lower()
>>> 'python'
```

### strip : 양쪽 공백 지우기 lstrip : 왼쪽 공백 지우기 rstrip : 오른쪽 공백 지우기

```python
a = "   python   "

a.strip()
>>> 'python'
a.lstrip()
>>> 'python   '
a.rstrip()
>>> '   python'
```

### replace : 문자형 대체하기

```python
a = "I love python"

a.replace("love", "like")
>>> 'I like python'

a = "I love love python"

a.replace("love", "like")
>>> 'I like like python'
```

### split : 문자형 나누기 (리스트로 return)

```python
a = "I love python"

a.split()
>>> ['I', 'love', 'python']

b = "1:2:3:4:5:6:7:8:9:"

b.split(':')
>>> ['1', '2', '3', '4', '5', '6', '7', '8', '9', '']
```
