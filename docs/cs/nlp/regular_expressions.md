# Regular Expressions

## Regular Expressions (정규 표현식) 이란

지정된 패턴을 만족하는 문자열을 검색하는 특수 구문

하드코딩된 문자열 대신 패턴을 일치시키고 싶을 때 텍스트를 필터링하고 정렬하는 데 매우 유용

### Raw Strings

Python 은 특정 문자가 특별한 의미를 가짐 (ex: \n - 줄바꿈)

하지만 이러한 코드가 문자열에 나타는 경우가 있는데 특별한 의미가 아닌 리터럴 임을 알려주고 싶을 때 사용

```python
my_folder = "C:\desktop\notes"

print(my_folder)
```

```output
C:\desktop
otes
```

```python
my_folder = r"C:\desktop\notes"
print(my_folder)
```

```output
C:\desktop\notes
```

### re.search

문자열에 특정 패턴이 있는지 확인하는 함수

re.search("찾을 패턴", "찾을 문자열")

패턴이 발견되지 않으면 None 을 리턴

```python
result_search = re.search("pattern", r"string containing the pattern")

print(result_search)
```

```output
<re.Match object; span=(22, 29), match='pattern'>
```

```python
print(result_search.group()) # returns just the matching pattern
```

```output
pattern
```

```python
result_search = re.search("pattern",r"the phrase to find isn't in this string")

print(result_search)
```

```output
None
```

### re.sub

특정 텍스트를 찾아서 바꿈

re.sub("찾을 패턴", "바꿀 텍스트", "문자열")

```python
string = r"sara was able to help me find the items i needed quickly"
new_string = re.sub(r"sara", r"sarah", string)

print(new_string)
```

```output
sarah was able to help me find the items i needed quickly
```

### Regex Syntax

```python
customer_reviews = ['sam was a great help to me in the store', 
                    'the cashier was very rude to me, I think her name was eleanor', 
                    'amazing work from sadeen!', 
                    'sarah was able to help me find the items i needed quickly', 
                    'lucy is such a great addition to the team', 
                    'great service from sara she found me what i wanted'
                   ]
```

a 로 시작하는 리뷰 찾기

```python
a_reviews = []
pattern_to_find = r"^a"
for string in customer_reviews:
    if (re.search(pattern_to_find, string)):
        a_reviews.append(string)

print(a_reviews)
```

```output
['amazing work from sadeen!']
```

y로 끝나는 리뷰 찾기

```python
y_reviews = []
pattern_to_find = r"y$"
for string in customer_reviews:
    if (re.search(pattern_to_find, string)):
        y_reviews.append(string)

print(y_reviews)
```

```output
['sarah was able to help me find the items i needed quickly']
```

원하는 단어가 포함된 리뷰 찾기

```python
needwant_reviews = []
pattern_to_find = r"(need|want)ed"
for string in customer_reviews:
    if (re.search(pattern_to_find, string)):
        needwant_reviews.append(string)

print(needwant_reviews)
```

```output
['sarah was able to help me find the items i needed quickly', 'great service from sara she found me what i wanted']
```
