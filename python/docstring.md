# Docstring

## docstring 이란

소스 코드에 포함된 문서 (document)

## 사용 방법

```python
class CustomClass:
    """
    클래스의 문서화 내용을 입력합니다.    
    """

    def custom_function(param):
        '''
        함수의 문서화 내용을 입력합니다.
        '''

        코드...

print(CustomClass.__doc__)

>>> 클래스의 문서화 내용을 입력합니다.
```

## 주석 vs Docstring

주석, docstring 둘 다 가독성과 코드의 이해도를 높이는 데 사용되지만 주석은 코드 라인에 설명을 추가하고, docstring 은 함수, 클래스, 모듈 등의 코드 요소에 대한 문서화를 제공하는 데 사용
