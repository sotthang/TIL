# Python (파이썬)

## 프로그래밍이란?

특정 목적을 달성하기 위해 설계된 알고리즘(algorithm)을 프로그래밍 언어를 사용하여 구체적인 프로그램으로 작성하는 과정

## Python (파이썬) 이란

네덜란드의 프로그래머 귀도 반 로섬(Guido van Rossum) 이 1989년 크리스마스 주에, 연구실이 닫혀있어서 심심한 김에 만든 인터프리터 방식의 프로그래밍 언어

## 파이썬의 특징

- 인터프리터 언어 (Interpreter)
- 객제 지향 프로그래밍 (Object Oriented Programming)

### 인터프리터 란

코드를 한 줄씩 읽어 내려가며 소스코드를 기계어로 변환하는 컴파일 과정 없이 실행하는 프로그램

### 객체 지향 프로그래밍 이란

프로그램 설계방법론이자 개념의 일종으로, 명령형 프로그래밍에 속함
프로그램을 단순히 데이터와 처리 방법으로 나누는 것이 아니라, 프로그램을 수많은 '객체(object)'라는 기본 단위로 나누고 이들의 상호작용으로 서술하는 방식
객체란 하나의 역할을 수행하는 '메소드와 변수(데이터)'의 묶음

### IDE (Integreted Development Environment)

프로그래머가 소프트웨어 코드를 효율적으로 개발하도록 돕는 소프트웨어 애플리케이션

### IDLE (Intergrated Development and Learning Environment)

파이썬 설치시 같이 설치되는 내장프로그램으로 파이썬 프로그램 작성을 도와주는 통합개발 환경

## 코드 스타일 가이드

코드를 어떻게 작성할지 에 대한 가이드라인
Coding Convention (코딩 규약) : 코딩할 때 지켜야 할 서로 간의 규칙, 더 좋은 품질의 코딩 및 협업에 필요

PEP (Python Enhancement Proposal) : 파이썬 코딩 규약, 파이썬 코딩을 어떻게 할지 알려주는 가이드 문서

PEP8 (<https://peps.python.org/pep-0008/>)

Ex)

- Whitespace
  - 들여쓰기는 탭 보다는 스페이스 4번을 사용
  - 한 줄의 문자 길이는 79자 이하
  - 함수와 클래스는 빈 줄 2개로 구분, 클래스와 메서드는 빈 줄 1개로 구분
  - import 는 하나의 라인에 하나의 module 만 등등

- Naming
  - 함수, 변수, attribute 는 소문자로 하며 단어 사이는 밑줄( _ ) 사용
  - 클래스는 단어 첫 문자를 대문자로 사용
  - module name 은 짧게 소문자로 사용 등

## 주석

코드에 대한 설명으로 코드에 반영되지 않음

```# 로 주석 처리```

```python
name = naru
# 이름 변수 할당
```

## 입출력

input, print 로 입출력 가능

```python
name = input('이름 입력 :') # naru 입력
print(name)
naru
```

## 변수 란

컴퓨터 메모리에 저장되어 있는 객체를 참조하기 위해 사용되는 것
파이썬에서 변수 할당은 할당 연산자인 = 를 사용하여 할당 (같다 라는 의미는 == 를 사용)

```python
x = 1
y = 'python'
```

같은 값을 동시에 할당하거나 다른 값을 동시에 할당 가능

```python
a = b = 1000
x, y = 11, 22
```

type() : 변수에 할당된 값의 타입 확인
id() : 변수에 할당된 객체의 고유한 identify 값 (메모리주소) 확인

```python
x = 1
type(x)
<class 'int'>
id(x)
1715307413744
```

## 식별자

객체 (변수, 함수, 모듈 등) 를 식별하는데 사용하는 이름

### 규칙

1. 영문 알파벳, 언더스코어(_), 숫자 로 구성
2. 첫 글자에 숫자 불가
3. 길이 제한이 없고, 대소문자 구분
4. print, sum 등 내장함수나 모듈, True, class, or 등 예약어는 사용 불가

예약어 확인 방법

```python
import keyword
print(keyword.kwlist)
```

## 자료형 이란

객체의 종류 (type)

- 숫자
  - 수치형 (Numeric Type)
    - 정수 (int)
    - 실수 (float)
    - 복소수 (complex)
- 시퀀스
  - 문자열 (str)
  - 튜플 (tuple)
  - 리스트 (list)
  - 레인지 (range)
- 컬렉션
  - 집합 (set)
  - 딕셔너리 (dictionary)
- None

## 수치형

### 정수 (int)

모든 정수 타입은 int 이며 오버플로우 (데이터 타입별로 사용할 수 있는 메모리 크기를 넘어서는 것) 가 발생하지 않음

```python
x = 123
type(x)
<class 'int'>
```

### 실수 (float)

정수가 아닌 모든 실수 타입은 float

```python
x = 12.3
type(x)
<class 'float'>
```

부동소수점 : 컴퓨터가 실수를 표현하는 방법이며 이로인해 floating point rounding error 가 발생 할 수 있음

```python
3.14 - 3.02 == 0.12
False
```

floating point rounding error : 컴퓨터에서 소수점 연산은 정확하게 할 수 없기에 근삿값으로 대체되고 이로인해 발생하는 문제

### 복소수 (complex)

실수부와 허수부로 구성

```python
x = 1+2j
type(a)
<class 'complex'>
```

## 불린 (boolean)

True, False 값을 가진 타입 (True 는 1, False 는 0 에 해당)
비교 또는 논리 연산에 활용

## 연산자 (operator)

### 산술 연산자

사칙연산 및 수식 계산

|연산자|내용|
|-----|--|
|+|덧셈|
|-|뺄셈|
|*|곱셈|
|**|거듭제곱|
|/|나눗셈|
|//|몫|
|%|나머지|

### 복합 연살자

연산과 할당을 동시에 가능

|연산자|내용|
|-----|--|
|a += b|a = a + b|
|a -= b|a = a - b|
|a *= b|a = a * b|
|a **= b|a = a ** b|
|a /= b|a = a / b|
|a //= b|a = a // b|
|a %= b|a = a % b|

### 비교 연산자

값을 비교하며 True 또는 False 를 리턴

|연산자|내용|
|-----|--|
|<|미만|
|<=|이하|
|>|초과|
|>=|이상|
|==|같은|
|!=|같지 않음|
|is|객체 아이덴티티|
|is not|객체 아이덴티티 아닌 경우|

### 논리 연산자

논리식을 판단하여 True 또는 False 를 리턴

|연산자|내용|
|-----|--|
|a and b|a 와 b 모두 True 면 True|
|a or b|a 또는 b 중 하나라도 True 면 True|
|not a|True 를 False 로, False 를 True로 |

## 컨테이너 란

여러 개의 값을 담을 수 있는 객체

### 컨테이너 분류

순서가 있는 데이터 (Ordered) vs 순서가 없는 데이터 (Unordered)

- 시퀀스
  - 문자열 (string)
  - 리스트 (list)
  - 튜플 (tuple)
  - 레인지 (range)
- 컬렉션 / 비시퀀스
  - 셋 (set)
  - 딕셔너리 (dictionary)
