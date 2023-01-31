# 표준 내장 객체

## Date

### 개요

`new Date()`를 통해 반환되는 인스턴스를 '타임스탬프'(Timestamp)라고 합니다.

```js
const date = new Date()
console.log(date)
// 타임스탬프 - 'Wed Sep 28 2022 10:45:41 GMT+0900 (한국 표준시)'

console.log(typeof date) // 'object'
console.log(typeof 'Wed Sep 28 2022 10:45:41 GMT+0900 (한국 표준시)') // 'string'
```

```js
const d1 = new Date(2022, 11, 16, 12, 57, 30)//11월이 아닌 12월 (월부분만 +1)
console.log(d1) // 'Fri Dec 16 2022 12:57:30 GMT+0900 (한국 표준시)'

const d2 = new Date('Fri Dec 16 2022 12:57:30 GMT+0900 (한국 표준시)')
console.log(d2) // 'Fri Dec 16 2022 12:57:30 GMT+0900 (한국 표준시)'
```

### .getFullYear()와 .setFullYear()

날짜 인스턴스의 '연도'를 반환하거나 지정합니다.

```js
const date = new Date()

console.log(date.getFullYear()) // 2022

date.setFullYear(2023)
console.log(date.getFullYear()) // 2023
console.log(date) // 'Thu Sep 28 2023 14:23:23 GMT+0900 (한국 표준시)'
```

### .getMonth()와 .setMonth()

날짜 인스턴스의 '월'을 반환하거나 지정합니다.  
0부터 시작(Zero-based numbering)합니다.

```js
const date = new Date()

console.log(date.getMonth()) // 8
console.log(date) // 'Wed Sep 28 2022 15:26:49 GMT+0900 (한국 표준시)'

date.setMonth(0)
console.log(date.getMonth()) // 0
console.log(date) // 'Fri Jan 28 2022 14:26:33 GMT+0900 (한국 표준시)'
```

### .getDate()와 .setDate()

날짜 인스턴스의 '일'을 반환하거나 지정합니다.

```js
const date = new Date()

console.log(date.getDate()) // 28
console.log(date) // 'Wed Sep 28 2022 15:35:14 GMT+0900 (한국 표준시)'

date.setDate(11)
console.log(date.getDate()) // 11
console.log(date) // 'Mon Sep 11 2022 12:03:40 GMT+0900 (한국 표준시)'
```

### .getHours()와 .setHours()

날짜 인스턴스의 '시간'을 반환하거나 지정합니다.

```js
const date = new Date()

console.log(date.getHours()) // 14
console.log(date) // 'Wed Dec 21 2022 07:23:51 GMT+0900 (한국 표준시)'

date.setHours(7)
console.log(date.getHours()) // 7
console.log(date) // 'Wed Dec 21 2022 07:23:51 GMT+0900 (한국 표준시)'
```

### .getMinutes()와 .setMinutes()

날짜 인스턴스의 '분'을 반환하거나 지정합니다.

```js
const date = new Date()

console.log(date.getMinutes()) // 25
console.log(date) // 'Wed Sep 28 2022 15:47:33 GMT+0900 (한국 표준시)'

date.setMinutes(2)
console.log(date.getMinutes()) // 2
console.log(date) // 'Wed Sep 28 2022 15:02:33 GMT+0900 (한국 표준시)'
```

### .getSeconds()와 .setSeconds()

날짜 인스턴스의 '초'를 반환하거나 지정합니다.

```js
const date = new Date()

console.log(date.getSeconds()) // 13
console.log(date) // 'Wed Sep 28 2022 15:50:13 GMT+0900 (한국 표준시)'

date.setSeconds(57)
console.log(date.getSeconds()) // 57
console.log(date) // 'Wed Sep 28 2022 15:50:57 GMT+0900 (한국 표준시)'
```

### .getDay()

날짜 인스턴스의 '요일'을 반환합니다.

```js
const date = new Date()
const day = date.getDay()

console.log(day) // 3
console.log(getDayKo(day)) // '수요일'

function getDayKo(day) {
  switch (day) {
    case 0: return '일요일'
    case 1: return '월요일'
    case 2: return '화요일'
    case 3: return '수요일'
    case 4: return '목요일'
    case 5: return '금요일'
    case 6: return '토요일'
  }
}
```

### .getTime()와 .setTime()

유닉스 타임(UNIX Time)으로부터 날짜 인스턴스의 경과한 시간을 '밀리초(ms)'로 반환하거나 지정합니다.  
유닉스 타임이란 1970.01.01 00:00:00 시간을 의미합니다.

```js
const date = new Date()

console.log(date.getTime()) // 1664343325817
console.log(date) // 'Wed Sep 28 2022 15:58:05 GMT+0900 (한국 표준시)'

date.setTime(1700000000000)
console.log(date.getTime()) // 1700000000000
console.log(date) // 'Wed Nov 15 2023 07:13:20 GMT+0900 (한국 표준시)'
```

```js
Date.prototype.isAfter = function (date) {
  const a = this.getTime()
  const b = date.getTime()
  return a > b
}

const d1 = new Date('Sat Jan 01 2022 00:00:00 GMT+0900 (한국 표준시)')
const d2 = new Date('Sun Jan 01 2023 00:00:00 GMT+0900 (한국 표준시)')

console.log(d1.isAfter(d2)) // false
console.log(d2.isAfter(d1)) // true
```

### .toUTCString()

날짜 인스턴스의 협정 세계시(UTC)를 반환합니다.  
협정 세계시(UTC) 혹은 그리니치 평균시(GMT)는 영국 런던 기점의 기준시입니다.  
한국은 UTC 기준보다 9시간 빠릅니다.

```js
console.log(new Date())
// Tue Oct 25 2022 16:29:54 GMT+0900 (한국 표준시)

console.log(new Date().toUTCString())
// Tue, 25 Oct 2022 07:29:54 GMT
```

### .toISOString()

날짜 인스턴스의 협정 세계시(UTC)를 'ISO 8601' 포맷으로 반환합니다.  
'ISO 8601'는 날짜와 시간을 표현하는 국제 표준 규격입니다.

```js
console.log(new Date())
// Tue Oct 25 2022 16:29:54 GMT+0900 (한국 표준시)

console.log(new Date().toISOString())
// 2022-10-25T07:29:54.000Z
```

### Date.now()

유닉스 타임(UNIX Time)으로부터 메소드가 호출될 때의 경화한 시간을 '밀리초(ms)'로 반환합니다.

```js
const time = new Date().getTime() // 변수에 담아 특정시간을 들고 있을수 있으나
console.log(Date.now()) // 1664349597861 현재시간만 알수있음
console.log(time) // 1664349597861

setTimeout(() => {
  console.log(Date.now()) // 1664349598861
  console.log(time) // 1664349597861
}, 1000)
```

