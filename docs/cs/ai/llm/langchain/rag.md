# RAG

## RAG(Retrieval-Augmented Generation) 란

LLM의 응답을 외부 지식으로 보강하여 더 정확하고 신뢰할 수 있는 응답을 생성하는 기술

## 주요 구성 요소

1. 문서 로딩 (Document Loading)
   - 다양한 형식의 문서를 로드
   - PDF, TXT, HTML, DB 등 지원
   ```python
   from langchain.document_loaders import TextLoader
   loader = TextLoader('data.txt')
   documents = loader.load()
   ```

2. 텍스트 분할 (Text Splitting)
   - 긴 문서를 적절한 크기로 분할
   - 컨텍스트 윈도우 제한 고려
   ```python
   from langchain.text_splitter import CharacterTextSplitter
   text_splitter = CharacterTextSplitter(
       chunk_size=1000,
       chunk_overlap=200
   )
   texts = text_splitter.split_documents(documents)
   ```

3. 임베딩 생성 (Embedding)
   - 텍스트를 벡터로 변환
   - 의미적 유사도 계산을 위해 필요
   ```python
   from langchain.embeddings import OpenAIEmbeddings
   embeddings = OpenAIEmbeddings()
   ```

4. 벡터 저장소 (Vector Store)
   - 임베딩을 저장하고 검색
   - 유사도 기반 검색 지원
   ```python
   from langchain.vectorstores import Chroma
   db = Chroma.from_documents(texts, embeddings)
   ```

5. 검색 및 생성 (Retrieval & Generation)
   - 관련 문서 검색
   - 컨텍스트를 포함한 응답 생성
   ```python
   # 검색
   query = "인공지능의 미래"
   docs = db.similarity_search(query)
   
   # 생성
   from langchain.chains import RetrievalQA
   qa_chain = RetrievalQA.from_chain_type(
       llm=llm,
       chain_type="stuff",
       retriever=db.as_retriever()
   )
   result = qa_chain.run(query)
   ```

## 장점

1. 정확성 향상
   - 최신 정보 활용 가능
   - 도메인 특화 지식 활용
   - 환각(hallucination) 감소

2. 투명성
   - 응답의 출처 추적 가능
   - 신뢰성 검증 용이

3. 유연성
   - 다양한 데이터 소스 활용
   - 지속적인 지식 업데이트 가능

## 사용 사례

1. 고객 지원
   - 제품 문서 기반 응답
   - FAQ 자동 응답

2. 연구 지원
   - 논문 검색 및 요약
   - 연구 데이터 분석

3. 교육
   - 교재 기반 학습 지원
   - 맞춤형 교육 콘텐츠

4. 기업 지식 관리
   - 내부 문서 검색
   - 지식 베이스 구축
