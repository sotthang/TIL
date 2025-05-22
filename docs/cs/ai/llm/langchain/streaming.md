# Streaming

## Streaming 이란

Streaming은 LLM의 응답을 실시간으로 받아오는 기술

장점
- 응답이 생성되는 즉시 사용자에게 전달
- 사용자 경험(UX) 향상
- 긴 응답의 경우 특히 유용

```python
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate

chat_template = ChatPromptTemplate.from_template("다음 주제에 대해 설명해주세요: {topic}")
inputs = [
    {"topic": "인공지능"}
]
llm = ChatOpenAI(model_name = "gpt-4",
                 temperature = 0,
                 streaming = True,
                 api_key="")
chain = chat_template | llm

for chunk in chain.stream(inputs):
    print(chunk.content, end="", flush=True)
```

```output
인공지능(AI, Artificial Intelligence)은 기계가 인간의 학습 능력, 추론 능력, 지각 능력, 자연어 이해 능력 등을 컴퓨터 프로그램을 통해 모방하는 기술을 말합니다. 이는 기계가 인간의 지능을 모방하여 스스로 학습하고, 문제를 해결할 수 있는 능력을 갖추게 하는 것을 목표로 합니다.

인공지능은 크게 두 가지 유형으로 나눌 수 있습니다. 첫 번째는 약 인공지능(Weak AI)으로, 특정 작업을 수행하는 데 초점을 맞춘 인공지능입니다. 대표적인 예로는 음성 인식 기능이 있는 스마트폰, 추천 알고리즘을 사용하는 온라인 쇼핑 사이트 등이 있습니다.

두 번째는 강 인공지능(Strong AI)으로, 인간의 지능을 완전히 모방하려는 인공지능입니다. 이는 인간의 일반적인 지능을 가지고 있으며, 어떤 문제든지 스스로 해결할 수 있는 능력을 가지고 있습니다. 현재로서는 이러한 강 인공지능은 아직 개발되지 않았습니다.

인공지능은 머신러닝과 딥러닝과 같은 기술을 활용하여 개발되며, 이를 통해 데이터를 학습하고, 패턴을 인식하고, 예측을 수행합니다. 이러한 기술은 의료, 금융, 교육, 교통 등 다양한 분야에서 활용되고 있습니다.
```
