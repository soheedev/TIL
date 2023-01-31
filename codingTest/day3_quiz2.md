# 중앙값 구하기
> 프로그래머스 코딩테스트 입문(Day3 Quiz2)

## 문제설명
* 중앙값은 어떤 주어진 값들을 크기의 순서대로 정렬했을 때 가장 중앙에 위치하는 값을 의미합니다. 예를 들어 1, 2, 7, 10, 11의 중앙값은 7입니다. 정수 배열 array가 매개변수로 주어질 때, 중앙값을 return 하도록 solution 함수를 완성해보세요.

## 제한사항
- array의 길이는 홀수입니다.
- 0 < array의 길이 < 100
- -1,000 < array의 원소 < 1,000

## solution.js
```javascript
function solution(array) {
    let answer = 0;
    let arrLength = array.length

    if( (arrLength % 2 != 0) && arrLength > 0 && arrLength < 100){
        array.sort(function(a, b){
            return a-b
        })

        // array.forEach(function (item) {
        //     if(item < -1000 || item > 1000){
        //         return false
        //     }
        // })

        let idx = parseInt(arrLength / 2)
        answer = array[idx]
    }
    return answer;
}
```

## 참고사항
* 배열 안의 요소들을 오름차순 정렬하기 위해서 sort()를 사용
* sort() 기본 사용시 문자열취급되어 [1, 10, 2, 3] 이렇게 정렬될 수 있음을 주의
* 비교대상하며 정렬시키기 위해 인자값으로 compareFunction()을 넣어줌
* 예) array.sort((a,b) => a - b)[Math.floor(array.length / 2)]
* [Array.prototype.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
