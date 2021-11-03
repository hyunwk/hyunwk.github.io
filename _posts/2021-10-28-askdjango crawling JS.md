---
title: Beautifulsoup askdjango crawling JS
tags: [Beautifulsoup, Python]
date: 2021-10-28 12:18:00 +09:00
categories: [Python]
---

target site : https://askdjango.github.io/lv2/

## Ajax란

Asynchronous Javascript and XML의 약자로, 비동기적으로 서버와 클라이언트 간 xml을 교환받는다.

XMLHttpRequest 객체를 이용하여 페이지를 새로고침 하지 않고 데이터를 load할 수 있다.

### 실행예시

```python
장고 2.0 주요 변경내역 살펴보기 https://www.askcompany.kr/r/sections/f04de5e/
(기초편) 장고 차근차근 시작하기 2/E https://www.askcompany.kr/r/sections/dfc55e7/
...
```

### 결과

```python
import requests
import json
from bs4 import BeautifulSoup

json_url = ('https://askdjango.github.io/lv2/data.json')
json_string = requests.get(json_url).text

data_list = json.loads(json_string)
for data in data_list.values():
    for item in data:
        print(item['name'], item['url'])
```

### network tab에서 json형식으로 데이터를 요청받는것을 확인 했다.

json 요청 url을 가져왔고 dictionary를 추출해서 작성해였다.
