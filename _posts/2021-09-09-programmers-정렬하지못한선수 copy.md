---
title: Programmers 해시-완주하지 못한 선수 Javascript
tags: [Algorithm, Programmers]
date: 2021-09-09 10:18:00 +09:00
categories: [Algorithm]

---

# 문제 설명
[Programmers 문제](https://programmers.co.kr/learn/courses/30/lessons/42576?language=javascript)  
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.


<br><br>
### 제한사항
- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.
<br><br>
### 입출력 예
<img src="https://user-images.githubusercontent.com/34102064/132681592-bc175765-068a-4a88-80a9-82637b38e783.png" width="100%" height="100%">  
<br><br><br>

# 첫번째 코드
```js
function solution(participant, completion) {
    for(var i=0; i<completion.length; i++){
        participant.splice(participant.indexOf(completion[i]), 1);
        }
    let answer = participant[0];
    return answer;
}
```  
<br><br>
# 풀이

participant는 completio는의 모든 요소를 포함하고 있다.
1. completion의 모든 요소를 for문으로 순회한다.
2. participant안에 있는 completion[i]를 찾고 삭제한다.

indexOf에서 반복문이 돌아가기 2중 반복문이 되어서 실패.

<br><br>  
# 두번째 코드
```js
function solution(participant, completion) {
    participant.sort();
    completion.sort();
      
    let i = 0;
    while (participant[i] === completion[i])
        i++;
    let answer = participant[i];
    return answer;
}
```  
<br><br>
# 풀이
1. 각 array를 정렬한다.
2. 정렬된 array에서 같은 인덱스에 다른 값이 있으면 participant의 요소가 completion에 없는 경우이다.
3. 해당 요소 반환