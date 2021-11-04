---
title: BeautifulSoup parser (lxml, html.parse, html5lib) 차이점
tags: [Beautifulsoup, Python]
date: 2021-10-27 12:18:00 +09:00
categories: [Python]
---

# 요약

HTML document의 모든 태그가 완벽하면 parser간 차이는 없다. ex ) \<a>\</a>

그렇지 않으면 parser간 출력 차이가 있다. ex) \<a>\</p> 와 같이 태그가 옳바르지 않는 경우 차이가 있다.

공식 문서에 따르면 correct한 방식의 parser는 없다.

html5lib이 HTML5 standard의 부분이여서 correct하다고 주장하지만 다른 parser도 적합하다.

# 차이점

### lxml

```python
BeautifulSoup("<a></p>", "lxml")
# <html><body><a></a></body></html>
```

### html.parser

```python
BeautifulSoup("<a></p>", "html.parser")
# <a></a>
```

### html5lib

```python
BeautifulSoup("<a></p>", "html5lib")
# <html><head></head><body><a><p></p></a></body></html>
```

출처 : [https://www.crummy.com/software/BeautifulSoup/bs4/doc/#differences-between-parsers](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#differences-between-parsers)
