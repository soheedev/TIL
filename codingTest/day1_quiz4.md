# 몫 구하기
> 프로그래머스 코딩테스트 입문(Day1 Quiz4)

> 프로그래머스 코딩테스트 입문

## 문제설명
* 정수 num1, num2가 매개변수로 주어질 때, num1을 num2로 나눈 몫을 return 하도록 solution 함수를 완성해주세요.

## 제한사항
* 0 < num1 ≤ 100
* 0 < num2 ≤ 100

## solution.js
```javascript
function solution(num1, num2) {
    let answer = 0;
    let comNum = 100;
    if(
        ( num1 >= 0 && num1 <= comNum ) &&
        ( num2 >= 0 && num2 <= comNum )
    ){
        answer = parseInt(num1 / num2);
    }
    return answer;
}
```

## 참고사항
* The parseInt() function parses a string argument and returns an integer of the specified radix (the base in mathematical numeral systems). 
* parseInt 함수는 첫 번째 인자를 문자열로 변환하고, 그 값을 파싱하여 정수나 NaN을 반환합니다
* parseInt는 정수 값을 반환하기 위해 소수점 이하 값을 잘라냅니다.
* The Math.floor() function always rounds down and returns the largest integer less than or equal to a given number.
