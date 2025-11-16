# Asynchronous (programming)

## 비동기란?

- 특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 프로그래밍 방식
- 시간이 소요되는 작업(예: I/O)이 있는 경우 해당 작업이 완료될 때까지 기다리지 않고 다른 작업을 계속 진행할 수 있음

## 동기 vs 비동기

- **동기(Synchronous)**: 작업을 순서대로 하나씩 처리. 하나의 작업이 끝나야 다음 작업을 시작할 수 있음
- **비동기(Asynchronous)**: 여러 작업을 동시에 처리. 하나의 작업이 끝나는 것을 기다리지 않고 다른 작업을 시작할 수 있음

## 비동기 프로그래밍

- **성능 향상**: I/O 작업과 같이 대기 시간이 긴 작업을 비동기로 처리하면, 대기하는 동안 다른 작업을 수행할 수 있어 전체적인 처리 시간이 단축됨
- **사용자 경험 개선**: 웹 애플리케이션이나 GUI 애플리케이션에서 오래 걸리는 작업을 비동기로 처리하면, UI가 멈추는 현상(blocking)을 방지하여 사용자 경험을 향상시킬 수 있음

## 주요 사용 사례

- **네트워크 요청**: API 호출과 같이 네트워크를 통해 데이터를 주고받는 작업
- **파일 I/O**: 대용량 파일을 읽거나 쓰는 작업
- **데이터베이스 쿼리**: 데이터베이스에 데이터를 요청하고 응답을 기다리는 작업

## async/await

- async와 await는 비동기 코드를 동기 코드처럼 보이게 만들어 가독성을 높이는 데 사용되는 키워드
- async 키워드는 함수가 비동기적으로 동작함을 나타냄
- await 키워드는 async 함수 내에서만 사용 가능하며, 비동기 작업이 완료될 때까지 기다리게 함

## asyncio

파이썬에서 async/await 구문을 사용하여 동시성 코드를 작성하는 라이브러리

### 예시

```python
import asyncio

async def fetch_data():
    print("데이터를 가져오는 중...")
    await asyncio.sleep(2)  # 2초 동안 대기 (I/O 작업 시뮬레이션)
    print("데이터 가져오기 완료!")
    return {"data": "some data"}

async def main():
    print("메인 함수 시작")
    data = await fetch_data()
    print(f"받은 데이터: {data}")
    print("메인 함수 종료")

asyncio.run(main())
```

```bash
메인 함수 시작
데이터를 가져오는 중...
데이터 가져오기 완료!
받은 데이터: {'data': 'some data'}
메인 함수 종료
```

### asyncio 핵심 개념

- 이벤트 루프 (Event Loop): 모든 비동기 애플리케이션의 핵심, asyncio.run()으로 시작되며, 단일 스레드에서 태스크 실행을 관리하고 스케줄링
- 코루틴 (Coroutines): async def로 선언된 비동기 함수, await 키워드를 만나면 실행을 일시 중단하고 이벤트 루프에 제어권을 반환할 수 있음
- 태스크 (Tasks): 코루틴을 감싸고 이벤트 루프에서 동시에 실행되도록 스케줄링, asyncio.create_task()를 통해 생성
- 퓨처 (Futures): 비동기 작업의 최종 결과를 나타내는 저수준 객체

### 성능 저하를 유발하는 일반적인 실수와 해결책

#### 실수 1: 순차적 실행 (Sequential Execution)

독립적인 태스크들을 병렬로 실행하지 않고 순차적으로 await하면, 총 실행 시간은 모든 태스크의 실행 시간을 합한 값이 됨

잘못된 예 (순차적):

```python
# 각 await가 이전 작업이 끝날 때까지 대기함
await get_user_notifications()
await get_recent_activity()
await get_unread_messages()
```

- 해결책 (병렬): asyncio.gather 또는 asyncio.TaskGroup을 사용하여 독립적인 태스크를 동시에 실행, 총 실행 시간은 가장 오래 걸리는 태스크의 시간으로 줄어듬

```python
# 세 개의 작업이 동시에 시작됨
await asyncio.gather(
    get_user_notifications(),
    get_recent_activity(),
    get_unread_messages()
)
```

병렬 실행 도구 비교

- asyncio.gather:
  - 여러 코루틴을 동시에 실행
  - 단점: 오류 처리가 미흡, 하나의 태스크에서 예외가 발생하면 다른 실행 중인 태스크들이 취소
- asyncio.create_task:
  - 태스크별 제어 및 오류 처리가 가능
  - 백그라운드 실행에 유용하지만, 여러 태스크를 개별적으로 await 해야 하는 번거로움이 있음
- asyncio.TaskGroup (Python 3.11+):
  - '구조적 동시성'을 위한 최신 대안
  - async with 문법을 사용하여 태스크 그룹을 관리하며, 컨텍스트를 벗어날 때 모든 태스크가 완료되거나 예외 처리가 보장됨

```python
async with asyncio.TaskGroup() as tg:
    tg.create_task(some_coro_1())
    tg.create_task(some_coro_2())
# 'async with' 블록이 끝나면 모든 태스크가 await됨
```

#### 실수 2: 동기 라이브러리 사용

asyncio 코드 내에서 requests나 pathlib 같은 동기(blocking) 라이브러리를 사용하면 이벤트 루프 전체가 차단됨

asyncio.gather 안에서 사용하더라도 실제로는 순차적으로 동작

- 해결책: aiohttp (requests 대용), aiofiles (files/pathlib 대용) 등 비동기(non-blocking)를 지원하는 전용 라이브러리를 사용

#### 실수 3: CPU 바운드 작업으로 이벤트 루프 차단

asyncio는 단일 스레드에서 실행되므로, 무거운 계산(CPU-bound) 작업은 이벤트 루프를 정지시켜 다른 I/O 작업들을 지연시킴

- 해결책: loop.run_in_executor()를 사용하여 CPU 바운드 작업을 별도의 스레드 풀(기본값)이나 프로세스 풀로 오프로드합니다.

```python
loop = asyncio.get_running_loop()
# CPU 집약적 함수를 별도 스레드에서 실행
await loop.run_in_executor(
    None,  # 기본 스레드 풀 사용
    cpu_bound_function,
    arg1
)
```

#### 실수 4: 중요하지 않은 작업으로 인한 차단

사용자 응답과 관련 없는 로깅 같은 비(非)핵심 작업을 await하면, 불필요하게 응답 시간이 지연됨

- 해결책: asyncio.create_task()를 사용해 해당 작업을 백그라운드 태스크로 분리하고 await 하지 않음

```python
user_profile = await get_user_profile()
# 로깅을 await하지 않고 백그라운드에서 실행
asyncio.create_task(send_logs_to_external_service())
return user_profile
```

#### 실수 5: 너무 많은 태스크 생성

아주 작은 작업들을 대량으로 태스크화하면 컨텍스트 스위칭 오버헤드가 발생하여 성능이 저하될 수 있음

- 해결책 1: 작은 작업들을 묶어(batching) 더 큰 태스크 몇 개로 만듬
- 해결책 2: asyncio.Semaphore를 사용하여 동시에 실행되는 최대 태스크 수를 제한

```python
# 동시에 최대 10개의 작업만 허용
semaphore = asyncio.Semaphore(10)

async with semaphore:
    await fetch_data()
```

#### 기타실수

- "Never Awaited" 코루틴: 코루틴을 호출하고 await하지 않아 작업이 실행조차 되지 않고 조용히 실패, flake8-async 같은 린터로 탐지할 수 있음
- 부적절한 리소스 관리: 파일, DB 커넥션 등을 try...finally 없이 사용하면 리소스 누수가 발생할 수 있음, async with를 사용한 비동기 컨텍스트 매니저로 해결

### asyncio 디버그 모드

기본적으로 비활성화된 디버그 모드를 활성화(asyncio.run(debug=True))하면 다음과 같은 문제를 탐지하는 데 도움

- await 되지 않은 코루틴 (RuntimeWarning)
- 잘못된 스레드에서 호출된 비동기 API
- 실행 시간이 100ms를 초과하는 콜백
- 느린 I/O 선택기(selector) 작업

### 동시성 모델 선택 가이드

- asyncio (단일 스레드): 대기 시간이 긴 다량의 I/O 바운드 작업(예: 네트워크 요청, 파일 I/O)에 최적
- threads (멀티 스레드): 공유 데이터 접근이 필요한 I/O 바운드 작업에 사용되며 GIL(Global Interpreter Lock)로 인해 진정한 병렬 처리는 아니지만 I/O 대기 시 다른 스레드가 실행될 수 있음
- processes (멀티 프로세스): CPU 바운드 작업(예: 이미지 처리, 무거운 계산)에 사용, 여러 CPU 코어를 활용하여 진정한 병렬성을 달성하지만, 메모리 및 통신 오버헤드가 큼
