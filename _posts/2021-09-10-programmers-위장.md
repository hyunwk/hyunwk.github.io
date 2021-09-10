---
title: Programmers 해시-위장 Javascript
tags: [Algorithm, Programmers]
date: 2021-09-10 10:18:00 +09:00
categories: [Algorithm]

---

# 문제 설명
[Programmers 문제](https://programmers.co.kr/learn/courses/30/lessons/42578?language=javascript)  
스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.

<img src="https://user-images.githubusercontent.com/34102064/132881739-9058bf23-9132-4338-ab41-9e2fa6392889.png" width="100%" height="100%">  

스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

<br><br>
### 제한사항
- clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
- 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
같은 이름을 가진 의상은 존재하지 않습니다.
- clothes의 모든 원소는 문자열로 이루어져 있습니다.
- 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
- 스파이는 하루에 최소 한 개의 의상은 입습니다..

<br><br>

### 입출력 예
<img src="https://user-images.githubusercontent.com/34102064/132881758-6e283395-01bd-4aae-b61c-f00301e8af05.png" width="100%" height="100%">    


<br><br>

 
#### 예제 1
headgear에 해당하는 의상이 yellow_hat, green_turban이고 eyewear에 해당하는 의상이 blue_sunglasses이므로 아래와 같이 5개의 조합이 가능합니다.
```
1. yellow_hat
2. blue_sunglasses
3. green_turban
4. yellow_hat + blue_sunglasses
5. green_turban + blue_sunglasses
```
#### 예제 2
face에 해당하는 의상이 crow_mask, blue_sunglasses, smoky_makeup이므로 아래와 같이 3개의 조합이 가능합니다.
```
1. crow_mask
2. blue_sunglasses
3. smoky_makeup
```

<br><br>

# 코드
```js
function solution(clothes) {
	return Object.values(clothes.reduce((obj, clothe)=> {
        if (!obj[clothe[1]])
            obj[clothe[1]] = 1;
    	obj[clothe[1]] += 1;
        return obj;
    }, {})).reduce((a,b)=>a*b) -1;
}
```  
<br><br>
# 풀이

1. clothes.reduce 에서 옷의 종류를 key, 개수를 value를 갖는 object를 생성했다.
2. 옷을 입지 않는 경우도 있으니 value의 초기값을 1로 지정했다.
(안입는 경우도 포함해서 곱하기 위해)
3. value를 전부 곱한 후 옷을 모두 입지 않은 경우 1을 뺐다.  