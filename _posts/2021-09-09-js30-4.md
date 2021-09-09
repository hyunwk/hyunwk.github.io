---
title: Javascript30 - Day4 Array 연습
tags: [Javascript]
date: 2021-09-09 21:18:00 +09:00
categories: [Javascript]
---

# 사용할 Array

```jsx
const **inventors** = [
{ first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
{ first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
{ first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
{ first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
{ first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
{ first: 'Nicolaus', last: 'Copernicus', year: 1473, passed: 1543 },
{ first: 'Max', last: 'Planck', year: 1858, passed: 1947 },
{ first: 'Katherine', last: 'Blodgett', year: 1898, passed: 1979 },
{ first: 'Ada', last: 'Lovelace', year: 1815, passed: 1852 },
{ first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
{ first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
{ first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
];

const **people** = [
  'Bernhard, Sandra', 'Bethea, Erin', 'Becker, Carl', 'Bentsen, Lloyd', 'Beckett, Samuel', 'Blake, William', 'Berger, Ric', 'Beddoes, Mick', 'Beethoven, Ludwig',
  'Belloc, Hilaire', 'Begin, Menachem', 'Bellow, Saul', 'Benchley, Robert', 'Blair, Robert', 'Benenson, Peter', 'Benjamin, Walter', 'Berlin, Irving',
  'Benn, Tony', 'Benson, Leana', 'Bent, Silas', 'Berle, Milton', 'Berry, Halle', 'Biko, Steve', 'Beck, Glenn', 'Bergman, Ingmar', 'Black, Elk', 'Berio, Luciano',
  'Berne, Eric', 'Berra, Yogi', 'Berry, Wendell', 'Bevan, Aneurin', 'Ben-Gurion, David', 'Bevel, Ken', 'Biden, Joseph', 'Bennington, Chester', 'Bierce, Ambrose',
  'Billings, Josh', 'Birrell, Augustine', 'Blair, Tony', 'Beecher, Henry', 'Biondo, Frank'
];
```
<br>  

# 메소드

## 문제 1 : Filter the list of inventors for those who were born in the 1500's  
<br>
> Array.prototype.filter()

```jsx
const fifteen = inventors.filter(inventor => 
(inventor.year >= 1500 && inventor.year < 1600));
console.table(fifteen);
```

- filter로 조건문에 맞는 요소들만 return 하여 array를 재구성한다. 
<br><br>  

## 문제 2 : Give us an array of the inventor first and last names
<br>

> Array.prototype.map()

```jsx
const fullNames = inventors.map(inventor => `${inventor.first} ${inventor.last}`);
console.log(fullNames);
```

- map을 사용하여 array의 양식을 재구성하여 return 한다.
<br><br>

## 문제 3 : Sort the inventors by birthdate, oldest to youngest
<br>

> Array.prototype.sort()

```jsx
const ordered = inventors.sort((a, b) => a.year - b.year);
console.table(ordered);
```

index는 0부터 시작해서, 연속된 두 요소의 값을 비교해서 정렬한다.
<br><br>

## 문제 4 : How many years did all the inventors live?
<br>

> Array.prototype.filter()

```jsx
const totalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);
```

reduce에 첫번째 인자로 return하는 함수를 전달했고, 두번째 인자인 초기값을 0으로 지정했다.  
<br>

## 문제 5 : Sort the inventors by years lived
<br>

> Array.prototype.sort()

```jsx
const oldest = inventors.sort(function(a, b) {
  const lastInventor = a.passed - a.year;
  const nextInventor = b.passed - b.year;
  return nextInventor - lastInventor;
});
console.table(oldest);
```

연속된 두 요소의 생애주기 값으로 비교 후 정렬했다.
<br><br>

## 문제 6 : create a list of Boulevards in Paris that contain 'de' anywhere in the name
<br>

사이트주소 [https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris](https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris)

> Array.prototype.filter()

```jsx
const category = document.querySelector('.mw-category');
const links = Array.from(category.querySelectorAll('a'));
const de = links
.map(link => link.textContent)
.filter(streetName => streetName.includes('de'));
```

mw-category 클래스를 선택 후 그 안에 있는 a태그들을 links에 array 형태로 할당하였다.

그 후 map으로 links의 요소들을 textContent로 바꾸었고 de를 포함하는 요소들만 반환하였다.
<br><br>

## 문제 7 : Sort the people alphabetically by last name
<br>

> Array.prototype.sort()

```jsx
const alpha = people.sort((lastOne, nextOne) => {
  const [aLast, aFirst] = lastOne.split(', ');
  const [bLast, bFirst] = nextOne.split(', ');
  return aLast > bLast ? 1 : -1;
```

구조 분해 할당을 이용하여 last, first를 할당하였다.

그후 값을 비교하여 정렬하였다.
<br><br>

## 문제 8 : Reduce Exercise
<br>

> Array.prototype.reduce()

```jsx
const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck', 'pogostick'];

const transportation = data.reduce(function(obj, item) {
  if (!obj[item]) {
    obj[item] = 0;
  }
  obj[item]++;
  return obj;
}, {});

console.log(transportation);
```

reduce의 매개변수로

첫번째 인자인 함수는, 해당 item이 없으면 생성해주고 만약 item이 있다면 값을 1 증가시키는 함수이다.

두번재 인자인 초기값으로는 빈 object를 전달하였다.