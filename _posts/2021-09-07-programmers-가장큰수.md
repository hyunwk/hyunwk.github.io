---
title: Programmers 정렬-가장 큰 수 Javascript
tags: [Algorithm, Programmers]
date: 2021-09-07 17:18:00 +09:00
categories: [Algorithm]

---

# 문제 설명
[Programmers 문제](https://programmers.co.kr/learn/courses/30/lessons/42746#)  
0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.  
예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.  
0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.
<br><br>
### 제한사항
- numbers의 길이는 1 이상 100,000 이하입니다.
- numbers의 원소는 0 이상 1,000 이하입니다.
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다. 
<br><br>
### 입출력 예
<img src="https://user-images.githubusercontent.com/34102064/132341916-de10d1d2-b4cc-4907-b5c2-c236fc000ecb.png" width="50%" height="50%">  
<br><br><br>

# 첫번째 코드
```js
function solution(numbers) {
    var answer = '';
    numbers.sort((x, y) => {
        while (x % 10 === 0)
                x /= 10;
        while (y % 10 === 0)
                y /= 10;
        if (String(y) < String(x))
            return -1;
		return 1;   
        });
    answer = numbers.join('');
    return answer;
}
}
```  
<br><br>
# 풀이
이 풀이에서 활용하고자 한 개념은 **js에서 문자 비교시 ascii 값으로 비교** 이다.
```
'a' < 'b'   true
'ac' < 'ab' false
```
하지만 숫자일때 비교 자리가 0인 경우 비교연산값으로는
문제에서 원하는 정렬값이 나오지 않는다.
```
'3' < '30'  true
```
따라서 3 이 30보다 큰 값으로 분류하려고
while문으로 뒷자리가 0인 경우를 전부 지워줬다.  
하지만 시간복잡도 초과로 실패. 

<br><br>  
# 두번째 코드
```js
function solution(numbers) {
    var answer = numbers.sort((x, y) => {
        const a = x.toString();
        const b = y.toString();
        return (b + a) - (a + b)}).join('');
    return answer[0] === '0' ? '0' : answer; 
}
```  
<br><br>
# 풀이
1번 풀이와 동일하게 ascii코드로 값을 비교하는 개념을 사용하였다.  
(b+a) - (a+b)를 사용한 이유는 0을 제거하지 않고도 아래 예시와 같이 문제에서 원하는 방식으로의 정렬이 된다.
```
a = '3', b = '30'  
(b+a) => '303'  
(a+b) => '330'  
```
return 에서 answer[0] === '0'인경우를 검사했는데  
input으로 0, 0이 들어왔을 경우 '00' 이 되기 때문에 '0'으로 치환한 것이다.
