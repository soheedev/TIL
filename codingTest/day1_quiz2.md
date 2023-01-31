# 두 수의 차
> 프로그래머스 코딩테스트 입문

## 문제 설명
> 프로그래머스 코딩테스트 입문(Day1 Quiz2)

* 정수 num1과 num2가 주어질 때, num1에서 num2를 뺀 값을 return하도록 soltuion 함수를 완성해주세요.

## 제한사항
* -50000 ≤ num1 ≤ 50000
* -50000 ≤ num2 ≤ 50000

## solution.js
```javascript
function solution(num1, num2) {
    let answer = 0;
    let comNum = 50000;
    if(
        ( num1 >= (comNum*-1) && num1 <= comNum ) &&
        ( num2 >= (comNum*-1) && num2 <= comNum )
    ){
        answer = num1 - num2;
    }
    return answer;
}
``` 
