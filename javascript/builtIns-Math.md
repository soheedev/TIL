# 표준 내장 객체
* `#패스트캠퍼스` `#국비지원교육` `#메가바이트스쿨` `#MegabyteSchool` `#개발자취업부트캠프` `#내일배움카드`

## Math

### Math.abs() 
absolute
주어진 숫자의 절댓값을 반환합니다.
```js
console.log(Math.abs(2)) // 2
console.log(Math.abs(-2)) // 2
```

### Math.ceil()

주어진 숫자를 올림해 정수를 반환합니다.

```js
console.log(Math.ceil(3.1415926535)) // 4
```

### Math.floor()

주어진 숫자를 내림해 정수를 반환합니다.

```js
console.log(Math.floor(3.1415926535)) // 3
```

### Math.round()

주어진 숫자를 반올림해 정수를 반환합니다.

```js
const num1 = 3.141
const num2 = 3.768

console.log(Math.round(num1)) // 3
console.log(Math.round(num2)) // 4
```

### Math.max()

주어진 숫자 중 가장 큰 숫자를 반환합니다.

```js
console.log(Math.max(1, 22, 38, 192)) // 192
```

### Math.min()

주어진 숫자 중 가장 작은 숫자를 반환합니다.

```js
console.log(Math.min(1, 22, 38, 192)) // 1
```

### Math.pow()

주어진 숫자의 거듭제곱한 값을 반환합니다.

```js
console.log(Math.pow(4, 2)) // 16
console.log(Math.pow(7, 2)) // 49
console.log(Math.pow(10, 3)) // 1000
```

### Math.random()

`0` 이상 `1` 미만의 난수를 반환합니다.

```js
console.log(Math.random()) // 0.6903810349799351

// 특정 범위의 무작위 정수를 얻는 함수
// 0~9 사이 정수
function random(min = 0, max = 10) {
  return Math.floor(Math.random() * (max - min)) + min
}

console.log(random()) // 0~9
console.log(random(11, 20)) // 11~19
console.log(random(101, 1000)) // 101~999

//// 원리! ////
// const ran = Math.random()
// const max = 5
// const min = 1
// 
// console.log(ran) // 무작위 수 생성!
// console.log(ran * (max - min)) // 범위의 최댓값 만들기!
// console.log(Math.floor(ran * (max - min))) // 소수점 내림!
// console.log(Math.floor(ran * (max - min)) + min) // 범위의 최솟값 만들기!
```

