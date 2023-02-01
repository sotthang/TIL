# 완전탐색

## 완전탐색 (brute force) 이란

모든 경우의 수를 따져서 문제를 해결하는 방법 (경우의 수가 적은 경우에만 사용)

ex) 자물쇠 비밀번호를 0000 부터 9999 까지 푸는 방법

```python
password = '5678'
number_try = '0000'
while password != number_try:
    number_try = str(int(number_try)+1)
print(number_try)
>>> 5678
```
