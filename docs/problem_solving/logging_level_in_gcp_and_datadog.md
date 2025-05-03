# Logging Level in GCP and Datadog

## Situation

GCP Cloud Run 에서 FastAPI 서버를 띄워서 사용중, Dockerfile 을 통해 Datadog 과 연동

Log config 는 logging.ini 파일로 설정

Logging level 이 GCP Logging 에서는 대부분의 log 가 default, Datadog 에서는 모든 log 가 Error 로 보임

## Solving

Logging level 판단 방법이 Tool 마다 다르다는 것을 확인

logging.ini 에서 format 에 severity=%(levelname)s status=%(levelname)s 같은 형태로 넣어도 필드 추가 안되고 levelname 으로 처리됨

format 을 custom 하여 처리하여 해결

logging.ini 중 일부
```text
[formatter_json]
class=custom_logging.CustomJsonFormatter
format=%(asctime)s %(name)s %(levelname)s %(message)s severity=%(levelname)s status=%(levelname)s
datefmt=%Y-%m-%dT%H:%M:%S
```

custom_logging.py
```python
from pythonjsonlogger import jsonlogger


class CustomJsonFormatter(jsonlogger.JsonFormatter):
    def add_fields(self, log_record, record, message_dict):
        super(CustomJsonFormatter, self).add_fields(log_record, record, message_dict)
        log_record["severity"] = record.levelname
        log_record["status"] = record.levelname

```

### GCP Logging

https://cloud.google.com/logging/docs/reference/v2/rest/v2/LogEntry
```text
severity enum (LogSeverity)
Optional. The severity of the log entry. The default value is LogSeverity.DEFAULT.
```

severity 필드로 판단

jsonPayload 에 severity 를 추가하면 이 값을 Logging level 로 사용 

기본값으로 나오는 Log
```text
{
    labels: {6}
    logName: "projects/test/logs/run.googleapis.com%2Fstderr"
    receiveTimestamp: "2024-04-17T03:40:54.932875271Z"
    resource: {2}
    textPayload: "[2024-04-17 03:40:54,598] [INFO] [uvicorn.access] 169.254.1.1:62092 - "POST /api/v1/chat/messages HTTP/1.1" 200"
    timestamp: "2024-04-17T03:40:54.599021Z"
}
```

INFO 로 나오는 Log
```text
{
    httpRequest: {10}
    labels: {6}
    logName: "projects/test/logs/run.googleapis.com%2Frequests"
    receiveTimestamp: "2024-04-17T03:40:54.604921430Z"
    resource: {2}
    severity: "INFO"
    timestamp: "2024-04-17T03:40:45.954661Z"
}
```

jsonPayload 추가
```text
{
    jsonPayload: 
        {
            asctime: "2024-04-17T09:55:43"
            levelname: "INFO"
            message: "test" 200"
            name: "uvicorn.access"
        }
    labels: {6}
    logName: "projects/test/logs/run.googleapis.com%2Fstderr"
    receiveTimestamp: "2024-04-17T09:55:43.440661575Z"
    resource: {2}
    severity: "INFO"
    timestamp: "2024-04-17T09:55:43.437309Z"
}
```

### Datadog

https://docs.datadoghq.com/ko/logs/guide/logs-show-info-status-for-warnings-or-errors/
```text
JSON 로그는 Datadog에서 자동으로 파싱됩니다. 로그 status 속성은 예약된 속성이기 때문에 JSON 로그가 사전 처리 작업을 통과합니다.
```

status 필드로 판단

jsonPayload 에 status 를 추가하면 이 값을 Logging level 로 사용

ERROR 로 나오는 Log (실제로는 INFO)
```text
{
    hostname    unknown
    service     test
    status      error
    timestamp   1713345211499
}
```

jsonPayload 추가
```text
{
    asctime     2024-04-17T09:12:23
    hostname    unknown
    levelname   INFO
    name        uvicorn.error
    service     test
    severity    INFO
    status      INFO
    timestamp   1713345143516
}
```
