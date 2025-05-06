# ChatGPT in Python

## 기본 사용법

1. API 클라이언트 초기화
    ```python
    from openai import OpenAI

    client = OpenAI(api_key="OPENAI_API_KEY")

    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {"role": "system", "content": "You are a helpful assistant."},
            {"role": "user", "content": "파이썬으로 리스트의 중복을 제거하는 방법을 알려주세요."}
        ]
    )

    print(response.choices[0].message.content)
    ```

    ```output
    리스트의 중복을 제거하려면 파이썬의 set 데이터 구조를 활용하면 됩니다. 다음은 리스트의 중복을 제거하는 방법입니다.

    my_list = [1, 2, 2, 3, 4, 4, 5]
    unique_list = list(set(my_list))
    print(unique_list)

    이 코드를 실행하면 중복이 제거된 리스트가 출력됩니다.
    ```

## 고급 사용법

1. 대화 기록 유지
    1. system
        - AI 어시스턴트의 기본 성격과 행동을 정의하는 역할
        - 대화의 맥락과 방향성을 설정하는 중요한 역할
        - ex: "You are a helpful assistant." (도움이 되는 어시스턴트로 설정)
    2. user
        - 실제 사용자가 입력하는 메시지
        - AI에게 질문하거나 요청하는 내용을 담는 역할
        - ex: "파이썬으로 리스트의 중복을 제거하는 방법을 알려주세요."
    3. assistant
        - AI가 응답하는 메시지
        - 이전 대화의 맥락을 유지하기 위해 사용됨
        - 대화 기록을 유지할 때 이전 응답들을 저장하는데 사용
    
    ```python
    messages = [
        {"role": "system", "content": "You are a helpful assistant."}
    ]

    messages.append({"role": "user", "content": "파이썬이란?"})
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=messages
    )

    messages.append({"role": "assistant", "content": response.choices[0].message.content})
    ```

2. 스트리밍 응답 처리
    1. 일반 응답 방식
        - ChatGPT가 전체 응답을 완성할 때까지 기다림
        - 응답이 완성되면 한 번에 전체 내용을 받음
        - 사용자는 응답이 완성될 때까지 기다려야 함
    2. 스트리밍 응답 방식
        - ChatGPT가 응답을 생성하는 즉시 실시간으로 전송
        - 응답이 생성되는 대로 조금씩 받아볼 수 있음
        - 사용자는 응답이 완성되기 전에도 내용을 확인 가능
    
    ```python
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=messages,
        stream=True
    )

    for chunk in response:
        if chunk.choices[0].delta.content:
            print(chunk.choices[0].delta.content, end="")
    ```
