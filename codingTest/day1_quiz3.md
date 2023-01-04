# 두 수의 곱
> 프로그래머스 코딩테스트 입문
## 문제설명
* `#패스트캠퍼스` `#국비지원교육` `#메가바이트스쿨` `#MegabyteSchool` `#개발자취업부트캠프` `#내일배움카드`
> 프로그래머스 코딩테스트 입문(Day1 Quiz3)

* 정수 num1, num2가 매개변수 주어집니다. num1과 num2를 곱한 값을 return 하도록 solution 함수를 완성해주세요.

## 제한사항
* 0 ≤ num1 ≤ 100
* 0 ≤ num2 ≤ 100

## solution.js
```javascript
function solution(num1, num2) {
    let answer = 0;
    let comNum = 100;
    if(
        ( num1 >= 0 && num1 <= comNum ) &&
        ( num2 >= 0 && num2 <= comNum )
    ){
        answer = num1 * num2;
    }
    return answer;
}
```
