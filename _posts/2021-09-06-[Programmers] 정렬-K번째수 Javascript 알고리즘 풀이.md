---
title: [Programmers] 정렬-K번째수 Javascript 알고리즘 풀이
tags: [Javascript, Algorithm, Programmers]
date: 2021-09-06 17:18:00 +09:00
categories: [Algorithm]
---

## 문제 설명
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.  
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.  
2에서 나온 배열의 3번째 숫자는 5입니다.  
배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.  

## 제한사항
array의 길이는 1 이상 100 이하입니다.  
array의 각 원소는 1 이상 100 이하입니다.  
commands의 길이는 1 이상 50 이하입니다.  
commands의 각 원소는 길이가 3입니다.  
## 입출력 예
array	commands	return
[1, 5, 2, 6, 3, 7, 4]	[[2, 5, 3], [4, 4, 1], [1, 7, 3]]	[5, 6, 3]
입출력 예 설명
[1, 5, 2, 6, 3, 7, 4]를 2번째부터 5번째까지 자른 후 정렬합니다. [2, 3, 5, 6]의 세 번째 숫자는 5입니다.  
[1, 5, 2, 6, 3, 7, 4]를 4번째부터 4번째까지 자른 후 정렬합니다. [6]의 첫 번째 숫자는 6입니다.  
[1, 5, 2, 6, 3, 7, 4]를 1번째부터 7번째까지 자릅니다. [1, 2, 3, 4, 5, 6, 7]의 세 번째 숫자는 3입니다.  

# 코드
```js
function solution(array, commands) {
    var answer = [];
 	let sliced = [];
    commands.forEach(items => {;
        sliced = array.slice(items[0] - 1, items[1]).sort((a,b) => a-b); 
        answer.push(sliced[items[2] - 1]);
    });
    return answer;
}
```  



# 풀이
> arr.forEach( callback( currentvalue[, index[, array]]) [, thisArg])  
> arr.slice([begin[, end]])  
> arr.sort([compareFunction])  
> arr.push(element1[, ...[, elementN]])  

1. foreach를 사용해 commands의 1차원 배열에 접근한다. 
2. slice를 사용해 array 원본을 수정하지 않고 item[0]-1 ~ item[1] 범위의 인덱스를 잘라 새로운 배열을 만든다.
3. 새로운 배열에 sort()를 사용해 오름차순으로 정렬한다.
4. 새로운 배열의 items[2] - 1 번 인덱스를 answer에 push한다.

# Programmers 풀이
```js
return commands.map(command => {
        const [sPosition, ePosition, position] = command
        const newArray = array
            .filter((value, fIndex) => fIndex >= sPosition - 1 && fIndex <= ePosition - 1)
            .sort((a,b) => a - b)    

        return newArray[position - 1]
    })
```
  ## 구조 분해 할당(Destructuring assignment)  
배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 한다.   
const [sPosition, ePosition, position] = command 
 
## map, filter
원본을 회손하지 않고 새로운 배열 반환  
return newArray[position - 1] -> map은 새로운 배열을 반환하기 때문에