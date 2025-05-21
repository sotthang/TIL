# LangChain

## LangChain 란

LLM(Large Language Model)을 활용한 애플리케이션을 쉽게 개발할 수 있도록 도와주는 프레임워크

## 주요 특징

1. 모듈화된 구성 요소
   - 체인(Chains)
   - 에이전트(Agents)
   - 메모리(Memory)
   - 프롬프트 템플릿(Prompt Templates)
2. 다양한 LLM 지원
   - OpenAI (GPT)
   - Anthropic (Claude)
   - Hugging Face
   - 기타 오픈소스 모델
3. 확장 가능한 구조
   - 커스텀 컴포넌트 개발
   - 다양한 도구와의 통합
   - 유연한 파이프라인 구성

## 예시

### 기본적인 체인 사용
```python
from langchain.llms import OpenAI
from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain

llm = OpenAI(temperature=0.7)

prompt = PromptTemplate(
    input_variables=["product"],
    template="다음 제품에 대한 마케팅 문구를 작성해주세요: {product}"
)

chain = LLMChain(llm=llm, prompt=prompt)

result = chain.run("스마트워치")
print(result)
```

### 메모리를 활용한 대화
```python
from langchain.memory import ConversationBufferMemory
from langchain.chains import ConversationChain

memory = ConversationBufferMemory()

conversation = ConversationChain(
    llm=llm,
    memory=memory,
    verbose=True
)

conversation.predict(input="안녕하세요!")
conversation.predict(input="오늘 날씨가 어때요?")
```

### 에이전트 사용
```python
from langchain.agents import load_tools, initialize_agent, AgentType

tools = load_tools(["serpapi", "llm-math"], llm=llm)

agent = initialize_agent(
    tools,
    llm,
    agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)

agent.run("서울의 현재 인구는 얼마인가요? 그리고 그 숫자의 제곱근은 얼마인가요?")
```

### 프롬프트 템플릿 활용
```python
from langchain.prompts import PromptTemplate
from langchain.chains import SimpleSequentialChain

first_prompt = PromptTemplate(
    input_variables=["topic"],
    template="다음 주제에 대한 5가지 키워드를 나열해주세요: {topic}"
)

second_prompt = PromptTemplate(
    input_variables=["keywords"],
    template="다음 키워드들을 사용하여 짧은 글을 작성해주세요: {keywords}"
)

first_chain = LLMChain(llm=llm, prompt=first_prompt)
second_chain = LLMChain(llm=llm, prompt=second_prompt)

overall_chain = SimpleSequentialChain(
    chains=[first_chain, second_chain],
    verbose=True
)

result = overall_chain.run("인공지능")
```

### 문서 처리
```python
from langchain.document_loaders import TextLoader
from langchain.text_splitter import CharacterTextSplitter
from langchain.embeddings import OpenAIEmbeddings
from langchain.vectorstores import Chroma

loader = TextLoader('data.txt')
documents = loader.load()

text_splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=0)
texts = text_splitter.split_documents(documents)

embeddings = OpenAIEmbeddings()

db = Chroma.from_documents(texts, embeddings)

query = "인공지능의 미래"
docs = db.similarity_search(query)
```

## 고급 LangChain 기술술

- [Parser](parser.md)
- [LCEL](lcel.md)

