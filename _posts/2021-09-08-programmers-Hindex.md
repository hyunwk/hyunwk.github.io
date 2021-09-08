---
title: Programmers 정렬 H-Index Javascript
tags: [Algorithm, Programmers]
date: 2021-09-08 15:18:00 +09:00
categories: [Algorithm]

---

# 문제 설명
[Programmers 문제](https://programmers.co.kr/learn/courses/30/lessons/42747)  
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.
<br><br>
### 제한사항
- 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.  
- 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.
<br><br>
### 입출력 예
<img src="https://user-images.githubusercontent.com/34102064/132449164-22e11897-e6c2-4885-a8c8-c5184b33b6d1.png" width="50%" height="50%">  
<br><br><br>

# 첫번째 코드
```js
function solution(citations) {
    var answer = 0;
	let idx = 0;
    let c_len = citations.length
    citations.sort((a,b)=> a-b);
    while (citations[idx] <= c_len - idx) {
        idx++;
        if (citations[idx] >= c_len - idx)
            break;
    }
    answer = c_len - idx;
    return answer;
}
```  
<br><br>
# 풀이
오름차순으로 정렬을 후 두가지 조건으로 풀었다.
```
1. citations[idx] <= c_len - idx
2. idx++
2. citations[idx] >= c_len - idx
```
citations = {0, 1, 3, 6, 5} 이고 idx = 1이라고 가정할 때 
1. 1 <= 4  (1, 3, 6, 5 의 길이)  
2. idx 1 증가
3. citations[2] = 3이므로 3 >= 3 (5 - 2) 이므로 while문을 벗어난다.  
-  따라서 답은 citations.legth - idx = 2

<br><br>  
# 프로그래머스 코드
```js
function solution(citations) {
    citations.sort((a,b)=> a-b);
    var i = 0;
     while(i + 1 <= citations[i]){
         i++;
     }
     return i;
}
```  
<br><br>
# 풀이
하단의 조건들을 
```
1. citations[idx] <= c_len - idx
2. idx++
3. citations[idx] >= c_len - idx  
```
i + 1 <= citations[i]라는 조건으로 압축시켰다.
