# Singleton Pattern

## Singleton Pattern 이란

객체를 여러 번 생성해도 클래스로부터 오직 하나의 객체만 생성되도록 하는 디자인 패턴

## 사용 환경

- 데이터베이스 연결 관리
  - 데이터베이스 연결은 자원이 많이 소모되는 작업이므로, 애플리케이션 전체에서 단 하나의 데이터베이스 연결 인스턴스만 유지하는 것이 좋기에 싱글톤 패턴을 사용하면 여러 컴포넌트가 동일한 데이터베이스 연결을 재사용할 수 있어, 성능을 향상시키고 자원 낭비를 줄일 수 있음
- 설정 파일 관리
  - 애플리케이션의 설정 정보를 담고 있는 설정 파일이나 환경 변수를 관리하는 객체의 경우, 애플리케이션 전체에서 일관된 설정 값을 유지해야 하기에 싱글톤 패턴을 사용하면 모든 컴포넌트가 동일한 설정 정보에 접근할 수 있으며, 설정 정보가 중복되어 로드되는 것을 방지
- 로깅
  - 애플리케이션에서 로깅을 처리하는 객체는 일반적으로 애플리케이션 전체에서 하나만 있으면 충분하기에 싱글톤 패턴을 사용하여 로깅 객체를 구현하면, 여러 컴포넌트에서 동일한 로깅 인스턴스에 접근하여 로그를 남길 수 있고 로그 파일에 일관된 형식을 유지하여 로깅의 성능을 최적화 가능

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
            print("Creating the singleton instance")
        return cls._instance


singleton1 = Singleton()
singleton2 = Singleton()

print(f"singleton1 is singleton2: {singleton1 is singleton2}")

>>> Creating the singleton instance
>>> singleton1 is singleton2: True
```

```python
class NonSingleton:
    def __init__(self):
        print("Creating a new instance")


non_singleton1 = NonSingleton()
non_singleton2 = NonSingleton()

print(f"non_singleton1 is non_singleton2: {non_singleton1 is non_singleton2}")

>>> Creating a new instance
>>> Creating a new instance
>>> non_singleton1 is non_singleton2: False
```
