# Parser

## Parser 란

데이터를 특정 형식으로 변환하거나 해석하는 도구

Langchain Parser 는 LLM 의 응답을 특정 형태로 변환환

Langchain Parser 대표 종류
- StrOutputParser
- JSONOutputParser
- CommaSeparatedListOutputParser

### StrOutputParser

LLM 응답을 문자열 형태로 변환

```python
from langchain_openai.chat_models import ChatOpenAI
from langchain_core.messages import HumanMessage
from langchain_core.output_parsers import StrOutputParser


chat = ChatOpenAI(model_name = "gpt-4",
                  temperature = 0,
                  api_key="")
message_h = HumanMessage(content = "파이썬에 대해 간단하게 알려줘")
response = chat.invoke([message_h])
str_output_parser = StrOutputParser()
response_parsed = str_output_parser.invoke(response)
print(response_parsed)
```

```output
파이썬은 1991년에 귀도 반 로섬(Guido van Rossum)이 개발한 고급 프로그래밍 언어입니다. 이 언어는 플랫폼 독립적이며 인터프리터식, 객체지향적, 동적 타이핑(dynamically typed) 대화형 언어입니다. 파이썬이라는 이름은 귀도가 좋아하는 코미디 〈Monty Python's Flying Circus〉에서 따온 것입니다.
```

### JSONOutputParser

LLM 응답을 JSON 형태로 변환

```python
from langchain_openai.chat_models import ChatOpenAI
from langchain_core.messages import HumanMessage
from langchain_core.output_parsers import JsonOutputParser


chat = ChatOpenAI(model_name = "gpt-4",
                  temperature = 0,
                  api_key="")

json_output_parser = JsonOutputParser()
message_h = HumanMessage(content = f"파이썬에 대해 간단하게 알려줘. {json_output_parser.get_format_instructions()}")
response = chat.invoke([message_h])
response_parsed = json_output_parser.invoke(response)
print(response_parsed)
```

```output
{'Python': {'Description': 'Python은 1991년 프로그래머인 귀도 반 로섬이 발표한 고급 프로그래밍 언어로, 플랫폼 독립적이며 인터프리터식, 객체지향적, 동적 타이핑(dynamically typed) 대화형 언어이다.', 'Features': {'Easy to Learn and Use': 'Python은 가독성이 좋은 문법을 가지고 있어 배우기 쉽고 사용하기 편리하다.', 'Object-Oriented': 'Python은 객체 지향적인 프로그래밍을 지원하며 클래스, 상속 등의 개념을 사용할 수 있다.', 'Portable': 'Python은 다양한 플랫폼에서 동작하므로 이식성이 좋다.', 'Extendable': 'Python은 C, C++, Java 등의 언어로 작성된 모듈을 호출하여 사용할 수 있다.', 'Large Standard Library': 'Python은 풍부한 표준 라이브러리를 제공하며, 이를 활용하면 다양한 기능을 쉽게 구현할 수 있다.'}, 'Applications': {'Web Development': 'Django, Flask 등의 프레임워크를 통해 웹 개발을 할 수 있다.', 'Data Analysis': 'Pandas, NumPy, Matplotlib 등의 라이브러리를 통해 데이터 분석을 할 수 있다.', 'Machine Learning': 'Scikit-learn, TensorFlow, PyTorch 등의 라이브러리를 통해 머신러닝을 할 수 있다.', 'Automation': 'Python은 스크립트 언어로서의 기능을 가지고 있어, 일련의 작업을 자동화하는데 사용할 수 있다.'}}}
```

### CommaSeparatedListOutputParser

LLM 응답을 list 형태로 변환

```python
from langchain_openai.chat_models import ChatOpenAI
from langchain_core.messages import HumanMessage
from langchain_core.output_parsers import CommaSeparatedListOutputParser


chat = ChatOpenAI(model_name = "gpt-4",
                  temperature = 0,
                  api_key="")

comma_output_parser = CommaSeparatedListOutputParser()
message_h = HumanMessage(content = f"파이썬에 대해 간단하게 알려줘. {comma_output_parser.get_format_instructions()}")
response = chat.invoke([message_h])
response_parsed = comma_output_parser.invoke(response)
print(response_parsed)
```

```output
['인터프리터 언어', '객체 지향 프로그래밍', '동적 타이핑', '쉬운 문법', '라이브러리 풍부', '데이터 분석에 유용', '웹 개발 가능', 'AI 및 머신러닝에 사용됨', '오픈소스', '크로스 플랫폼 지원']
```
