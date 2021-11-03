---
title: Beautifulsoup askdjango crawling HTML
tags: [Beautifulsoup, Python]
date: 2021-10-28 12:18:00 +09:00
categories: [Python]
---

target site : https://askdjango.github.io/lv1/

### 실행예시

```python
장고 2.0 주요 변경내역 살펴보기 https://www.askcompany.kr/r/sections/f04de5e/
(기초편) 장고 차근차근 시작하기 2/E https://www.askcompany.kr/r/sections/dfc55e7/
...
```

### 결과

```python
import requests
from bs4 import BeautifulSoup

html_file = requests.get('https://askdjango.github.io/lv1/').text
soup = BeautifulSoup(html_file, "lxml")

vods = soup.select('li[class=course]')
for vod in vods:
    print(vod.text, end='')
    print(vod.a['href'])
```

### Refact

find_all → select

find_all

```python
seasons = soup.find_all('ul')
for season in seasons:
    vods = season.find_all('li')
    for vod in vods:
        extract_from_vod(vod)

def extract_from_vod(vod):
    title = vod.find('a').text
    link = vod.a['href']
    print(title, link)
```

li에 접근하기 전에 상위 태그인 ul을 접근해야 된다고 생각을 했다.

따라서 모든 ul을 순회하고 그 안에 li를 순회하는 2중 for문 로직으로 작성하였다.

하지만 함축할 수 있는 코드가 늘어났고

li의 class를 고려하지 않고 모든 li를 find_all 하였다.

select

```python
vods = soup.select('li[class=course]')
for vod in vods:
    print(vod.text, end='')
    print(vod.a['href'])
```

find_all에서 select를 사용해봤고

li의 class='course'에 바로 접근했다.
