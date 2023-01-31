# 표준 내장 객체


## Number

### .toFixed()

숫자를 지정된 고정 소수점 표기(자릿수)까지 표현하는 `문자`로 반환합니다.
지정된 자리수까지만 짤라낸다. 문자로 반환되니 숫자로 변환시켜 사용필요

```js
const num = 3.1415926535

console.log(num.toFixed(2)) // '3.14'
console.log(parseFloat(num.toFixed(2))) // 3.14
```

### .toLocaleString()

숫자를 현지 언어 형식의 문자로 반환합니다.

```js
const num = 1000000

console.log(num.toLocaleString()) // '1,000,000'
console.log(`${num.toLocaleString()}원`) // '1,000,000원'
```

### Number.isInteger()

숫자가 정수(integer)인지 확인합니다.
클래스에서 바로 사용(정적메소드-Static)

```js
const num = 123
const pi = 3.14

console.log(Number.isInteger(num)) // true
console.log(Number.isInteger(pi)) // false
```

### Number.isNaN() 또는 isNaN()

주어진 값이 `NaN`인지 확인합니다.  
`isNaN()`보다 더 엄격한 버전으로 ES6에 추가된 `Number.isNaN()` 사용을 권장합니다.
네임스페이스(Namespace) 이름범위

```js
const num1 = NaN
const num2 = 123
const str = 'Hello world'
const nul = null

console.log(Number.isNaN(num1)) // true
console.log(Number.isNaN(num2)) // false
console.log(Number.isNaN(str)) // false
console.log(Number.isNaN(nul)) // false
```

### Number.parseInt() 또는 parseInt()

주어진 값(숫자, 문자)을 파싱해 특정 진수(radix)의 정수로 반환합니다.  
`Number.parseInt()`는 ES6에서 전역 객체의 모듈화를 위해 추가됐습니다.  
`10진수`가 기본값이 아니기 때문에 꼭 명시하는 것이 필요하다!

```js
const str = '3.1415926535'

// 10진수 정수로 반환!
console.log(Number.parseInt(str, 10)) // 3
console.log(Number.parseInt(num, 10)) // 3
```

다음과 같은 경우 `NaN`를 반환합니다.

- 진수 값이 `2`보다 작거나 `36`보다 큰 경우 (2<= 10 <=36)
- 공백이 아닌 첫 문자를 숫자로 변환할 수 없는 경우 (첫글자가 숫자로 시작하면 됨)

### Number.parseFloat() 또는 parseFloat()

주어진 값(숫자, 문자)을 파싱해 부동소수점 실수로 반환(숫자)합니다.  
`Number.parseFloat()`는 ES6에서 전역 객체의 모듈화를 위해 추가됐습니다.  

```js
const str = '3.1415926535'
const num = 3.1415926535

console.log(Number.parseFloat(str)) // 3.1415926535
console.log(Number.parseFloat(num)) // 3.1415926535
```

