---
title: BeautifulSoup4 개념 정리
tags: [Beautifulsoup, Python]
date: 2021-10-27 12:18:00 +09:00
categories: [Python]
---

### `BeautifulSoup`

Beautiful Soup transforms a complex HTML document into a complex tree of Python objects. But you’ll only ever have to deal with about four kinds of objects: `Tag`, `NavigableString`, `BeautifulSoup` and `Comment`.

## 태그 검색

```python
with open('home.html', 'r') as html_file:
    content = html_file.read()

    soup = BeautifulSoup(content, 'lxml')
    tags = soup.find('h5')
    print(tags)
```

soup.find(태그) ⇒ 해당하는 첫번째 태그 출력

```python
<h5 class="card-title">Python for beginners</h5>
```

soup.find_all(태그) ⇒ 해당하는 모든 태그 출력

```python
[<h5 class="card-title">Python for beginners</h5>,
<h5 class="card-title">Python Web Development</h5>,
<h5 class="card-title">Python Machine Learning</h5>]
```

## 태그 내부 text 검색

.text ⇒ text 속성만 가져올 수 있다.

```python
courses_html_tags = soup.find_all('h5')
    for course in courses_html_tags:
				print(course)
        print(course.text)
```

결과

```python
<h5 class="card-title">Python for beginners</h5>
Python for beginners
```

## 특정 태그 내부 태그 검색

1. div태그 중 class='card'인 태그 정보를 가져온다.
2. 태그 내부에 h5태그와 h5.text를 가져온다.
3. 태그 내부에 a태그와 a.text를 가져온다.

```python
courses_card = soup.find_all('div', class_='card')
    for course in courses_card:
        print(course.h5)
        print(course.h5.text)
        print(course.a)
        print(course.a.text)
```

```python
<h5 class="card-title">Python for beginners</h5>
Python for beginners
<a class="btn btn-primary" href="#">Start for 20$</a>
Start for 20$
```

## 문자열 조작

split 사용

```python
course.a.text
course.a.text.split()[-1]
```

결과

```python
Start for 100$
100$
```

replace 사용 → 모든 문자 치환

```python
job.find('h3', class_='joblist-comp-name').text.
job.find('h3', class_='joblist-comp-name').text.replace(' ', '')
```

결과

```python
	Surya Informatics Solutions Pvt. Ltd.
SuryaInformaticsSolutionsPvt.Ltd.
```

strip 사용 → 양 옆 공백 삭제

```python
job.find('h3', class_='joblist-comp-name').text.
job.find('h3', class_='joblist-comp-name').text.strip()
```

결과

```python
	Surya Informatics Solutions Pvt. Ltd.
Surya Informatics Solutions Pvt. Ltd.
```

## Requests 패키지

```python
import requests

html_text = requests.get(
    'https://www.timesjobs.com/candidate/job-search.html?searchType=personalizedSearch&from=submit&txtKeywords=python&txtLocation=')
print(html_text)
print(html_text.text)
```

결과

```python
<Response [200]> # 성공
HTML 태그들
```

find_all 결과값 find

```python
job = soup.find_all('li', class_='clearfix job-bx wht-shd-bx')
comp_name = job.find('h3', class_='joblist-comp-name')
```

→ error

find 결과값 find

```python
job = soup.find('li', class_='clearfix job-bx wht-shd-bx')
comp_name = job.find('h3', class_='joblist-comp-name')
```

결과값

```python
<h3 class="joblist-comp-name">
    Surya Informatics Solutions Pvt. Ltd.

    </h3>
```

태그 내 태그

```python
date = job.find('span', class_='sim-posted')
----
date = job.find('span', class_='sim-posted').span.text
```

```python
<span class="sim-posted">
<span>Posted few days ago</span>
</span>
---
Posted few days ago

```

attribute 접근

```python
<h2>
	<a href="aa">
```

인 경우 ['attribute'] 로 접근한다.

```python
more_info = job.header.h2.a['href'] ## aa
```

enumerate를 활용해서 index 번호 넘겨주기.

```python
for idx, job in enumerate(jobs):
        extract_from_job(idx, job, unfamiliar_skill)
```

## .string 속성

If a tag has only one child, and that child is a NavigableString, the child is made available as .string:

## 출처

[https://www.youtube.com/watch?v=XVv6mJpFOb0](https://www.youtube.com/watch?v=XVv6mJpFOb0)

[https://www.crummy.com/software/BeautifulSoup/bs4/doc/index.html?highlight=tag](https://www.crummy.com/software/BeautifulSoup/bs4/doc/index.html?highlight=tag)
