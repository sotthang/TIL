# LCEL 

## LCEL (LangChain Expression Language) 이란

LangChain 의 새로운 표현 언어로, LangChain 의 컴포넌트들을 더 유연하고 직관적으로 조합할 수 있게 해주는 도구

특징
- | 연산자를 사용하여 컴포넌트들을 연결
- 함수형 프로그래밍 스타일의 체이닝 가능

장점
- 코드가 더 간결하고 읽기 쉬움움
- 컴포넌트 재사용이 용이
- 디버깅이 쉬움
- 비동기 처리 지원

```python
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI


chain = (
    ChatPromptTemplate.from_template("다음 주제에 대해 설명해주세요: {topic}")
    | ChatOpenAI(model_name = "gpt-4",
                  temperature = 0,
                  api_key="")
    | StrOutputParser()
)

result = chain.invoke({"topic": "인공지능"})
print(result)
```

```output
인공지능(AI, Artificial Intelligence)은 기계가 인간의 학습 능력, 추론 능력, 지각 능력, 자연어 이해 능력 등을 모방하는 기술을 말합니다. 즉, 인간의 지능을 컴퓨터 등에 인공적으로 구현한 기술이라고 할 수 있습니다.
```

## LCEL 고급 기능

- [Batching](batching.md)
- [Streaming](streaming.md)
