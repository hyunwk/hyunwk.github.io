---
title: BeautifulSoup4 find_all vs select
tags: [Beautifulsoup, Python]
date: 2021-10-27 12:18:00 +09:00
categories: [Python]
---

## select

If you want to search for tags that match two or more CSS classes, you should use a CSS selector

references : [https://beautiful-soup-4.readthedocs.io/en/latest/#searching-by-css-class](https://beautiful-soup-4.readthedocs.io/en/latest/#searching-by-css-class)

## find_all

The find_all() method looks through a tag’s descendants and retrieves all descendants that match your filters.

생략 가능

```python
soup.find_all('a')
soup('a')
```

references : [https://beautiful-soup-4.readthedocs.io/en/latest/#calling-a-tag-is-like-calling-find-all](https://beautiful-soup-4.readthedocs.io/en/latest/#calling-a-tag-is-like-calling-find-all)

## select, find_all 차이

ResultSet = subclass of a list

`ResultSet` class is a *subclass of a list* and not a `[Tag` class](http://www.crummy.com/software/BeautifulSoup/bs4/doc/#tag) which has the `find*` methods defined. Looping through the results of `find_all()` is the most common approach:

```
th_all = soup.find_all('th')
result = []
for th in th_all:
    result.extend(th.find_all(text='A'))

```

Usually, [CSS selectors](http://www.crummy.com/software/BeautifulSoup/bs4/doc/#css-selectors) may help you solve it in one go except that not everything you can do with `find_all()` is possible with the `select()` method. For instance, there is no "text" search available in `bs4` CSS selectors. But, if, for example, you had to find all, say, `b` elements inside `th` elements, you could do:

CSS Selectors에는 text 검색이 없다. 하지만 th태그 내 b태그를 찾는 경우 아래오 같이 할 수 있다.

```
soup.select("th td")
```

StackOverFlow : [https://stackoverflow.com/questions/36076052/beautifulsoup-find-all-on-bs4-element-resultset-object-or-list/36101603#36101603](https://stackoverflow.com/questions/36076052/beautifulsoup-find-all-on-bs4-element-resultset-object-or-list/36101603#36101603)

## 요약

기능적으로 동일하다.

find : HTML tag를 검색한다.

select : CSS class를 검색한다.
