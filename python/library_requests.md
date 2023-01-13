# requests

파이썬용 http 라이브러리로 http, https 웹사이트에서 크롤링(crawling) 에 많이 사용 (bs4 와 함께)

## requests method

### requests.get

```python
res = requests.get('https://www.naver.com')
print(res)
>>> <Response [200]>
print(res.text)
>>> <!doctype html>                          <html lang="ko" data-dark="false"> <head> 
<meta charset="utf-8"> <title>NAVER</title> <meta http-equiv="X-UA-Compatible" 
content="IE=edge"> <meta name="viewport" content="width=1190"> 
<meta name="apple-mobile-web-app-title" content="NAVER"/> 
<meta name="robots" content="index,nofollow"/> 
<meta name="description" content="네이버 메인에서 다양한 정보와 유용한 컨텐츠를 만나 보세요"/>
...
```

URL에 get 요청 보냄

<https://www.naver.com> 으로 get 요청을 보냈고 정상적으로 응답하여 Response 200 이 출력됨

res 에는 결과값을 저장

### requests.post

```python
res = requests.post('https://www.naver.com')
print(res)
>>> <Response [200]>
```

URL에 post 요청 보냄

get 과 post 의 차이 : get 은 url 에 데이터를 붙여서 보내지만, post 는 url 이 아니라 body 에 데이터를 넣어서 보냄

### requests.put

```python
res = requests.put('https://www.naver.com')
print(res)
>>> <Response [501]>
```

URL에 put 요청 보냄

### requests.delete

```python
res = requests.delete('https://www.naver.com')
print(res)
>>> <Response [501]>
```

URL에 delete 요청 보냄

### requests.head

```python
res = requests.head('https://www.naver.com')
print(res)
>>> <Response [200]>
```

URL에 head 요청 보냄

### requests.options

```python
res = requests.options('https://www.naver.com')
print(res)
>>> <Response [404]>
```

URL에 options 요청 보냄

## response

HTTP 요청에 대한 서버 응답을 포함한 객체

- res.request : 내가 보낸 request 객체 접근 가능
- res.headers : 응답 헤더
- res.status_code : 응답 코드
- res.raise_for_status() : 200 아닌 경우 에러
- res.json() : json형태의 응답 데이터 (딕셔너리 타입으로 바로 변환)
- res.text : 수신한 byte단위의 데이터를 자동으로 decode 하여 사용자가 보기 좋게 만들어 줌
- res.content : 수신한 byte단위의 데이터를 있는 그대로 보여줌

## https status

<https://github.com/psf/requests/blob/c45a4dfe6bfc6017d4ea7e9f051d6cc30972b310/requests/status_codes.py>
