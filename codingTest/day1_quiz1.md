# 두 수의 합

### 문제설명
> 프로그래머스 코딩테스트 입문(Day1 Quiz1)

* 정수 num1과 num2가 주어질 때, num1과 num2의 합을 return하도록 soltuion 함수를 완성해주세요.

### 제한사항
* -50,000 ≤ num1 ≤ 50,000
* -50,000 ≤ num2 ≤ 50,000

### solution.js
```javascript
function solution(num1, num2) {
    let answer = 0;
    let comNum = 50000;
    if(
        ( num1 >= (comNum*-1) && num1 <= comNum ) &&
        ( num2 >= (comNum*-1) && num2 <= comNum )
    ){
        answer = num1 + num2;
    }
    return answer;
}
```

