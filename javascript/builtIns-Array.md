# 표준 내장 객체

## Array

### .length

배열의 길이(숫자)를 반환합니다.

```js
const arr = ['A', 'B', 'C']

console.log(arr.length) // 3
```

### .at()

대상 배열을 인덱싱합니다.  
음수 값을 사용하면 뒤에서부터 인덱싱합니다.  
`뒤에서 부터 조회할때 유용`
```js
const arr = ['A', 'B', 'C']

console.log(arr[0]) // 'A'
console.log(arr.at(0)) // 'A'

console.log(arr[arr.length - 1]) // 'C'
console.log(arr.at(-1)) // 'C'
```

### .concat()
`중요`  
대상 배열과 주어진 배열을 병합해 새로운 배열을 반환합니다.

```js
const arr1 = ['A', 'B', 'C']
const arr2 = ['D', 'E', 'F']
const arr3 = arr1.concat(arr2)
// const arr3 = [...arr1, ...arr2] 전개연산자로도 동일기능

console.log(arr1) // ['A', 'B', 'C']
console.log(arr2) // ['D', 'E', 'F']
console.log(arr3) // ['A', 'B', 'C', 'D', 'E', 'F']
```

### .every()

대상 배열의 모든 요소가 `콜백` 테스트를 통과(Truthy)을 반환하는지 확인합니다.  
콜백: 함수의 인수로 들어가는 함수, 즉 함수

```js
const arr1 = [1, 2, 3, 4]
const arr2 = [4, 5, 6, 7]

const isValid1 = arr1.every(item => item < 5) // 화살표 함수에 중괄호가 없을 경우 리턴 키워드가 없다.
const isValid2 = arr2.every(item => item < 5)

// 1) 4 => 4 < 5 //통과
// 2) 5 => 5 < 5 //실패
// 3) 6 => 6 < 5 //실패
// 4) 7 => 7 < 5 //실패

console.log(isValid1) // true
console.log(isValid2) // false

const arr = [1,2,3,4]
const isValid = arr.every(item => {
  console.log(item)
  return item < 3
})
//1
//2
//3 실패하는 경우가 나오면 뒤에 반복 실행을 멈춤
//false
```

### .filter()
`중요`  
대상 배열에서 콜백 테스트를 `통과하는 모든 요소만 모아서 새로운 배열`을 만들어 반환합니다.  
만약 모든 요소가 테스트를 통과하지 못하면 빈 배열을 반환합니다.  
원본 배열에서 개수가 줄어든다.

```js
const numbers = [1, 20, 7, 9, 104, 0, 58]
const filteredNumbers = numbers.filter(number => number < 30)

console.log(filteredNumbers) // [1, 20, 7, 9, 0]
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]
const adults = users.filter(user => user.age >= 19) // 많이 사용되는 유형

// 1) user => {name: 'Neo', age: 85}.age >= 19
// 2) user => {name: Amy', age: 22}.age >= 19
// 3) user => {name: 'Lewis', age: 11}.age >= 19

console.log(adults) // [ Neo객체, Amy객체 ]
```

### .find()
`중요`  
대상 배열에서 `콜백 테스트를 통과하는 첫 번째 요소`를 반환합니다.  
최초로 테스트가 통과하면, 이후 콜백은 실행되지 않습니다.  
모든 테스트가 실패하면, `undefined`를 반환합니다.

```js
const arr = [5, 8, 130, 12, 44]
const foundItem = arr.find(item => item > 10)
// 찾은게 없으면 undefined를 반환함

console.log(foundItem) // 130
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]
const foundUser = users.find(user => user.name === 'Amy')

console.log(foundUser) // { name: 'Amy', age: 22 }
```

### .findIndex()
`중요`  
대상 배열에서 `콜백 테스트를 통과하는 첫 번째 요소의 인덱스`를 반환합니다.  
최초로 테스트가 통과하면, 이후 콜백은 실행되지 않습니다.  
모든 테스트가 실패하면, `-1`을 반환합니다.

```js
const arr = [5, 8, 130, 12, 44]
//           0  1  2    3   4

const index = arr.findIndex(item => item > 10)

console.log(index) // 2
```

### .flat()

대상 배열의 `모든 하위 배열`을 지정한 깊이(Depth)까지 이어붙인 새로운 배열을 반환합니다.  
깊이의 기본값은 `1`입니다.  

```js
const arr = [1, 2, [3, 4]]

console.log(arr.flat()) // [1, 2, 3, 4]
```

```js
const arr = [1, 2, [3, 4, [5, 6]]]

console.log(arr.flat()) // [1, 2, 3, 4, [5, 6]]
console.log(arr.flat(2)) // [1, 2, 3, 4, 5, 6]
```

```js
const arr = [1, 2, [3, 4, [5, 6, [7, 8]]]]

console.log(arr.flat()) // [1, 2, 3, 4, [5, 6, [7, 8]]]
console.log(arr.flat(2)) // [1, 2, 3, 4, 5, 6, [7, 8]]
console.log(arr.flat(Infinity)) // [1, 2, 3, 4, 5, 6, 7, 8]
```

### .forEach()
`굉장히 중요!!!`  
대상 배열의 길이만큼 주어진 콜백을 실행합니다.  

```js
const arr = ['A', 'B', 'C']

arr.forEach(item => console.log(item)) //반환값은 undefiend

for (let i = 0; i < arr.length; i += 1) {
  console.log(arr[i])
}

// 'A'
// 'B'
// 'C'
```

`.forEach()`는 중간에 반복을 멈출 수 없습니다.  
반복을 멈출 수 있어야 한다면, `for` 반복문을 사용해야 합니다. (break 이용하여)  
forEach()는 비동기코드의 실행을 보장하지 않음  

```js
const arr = ['A', 'B', 'C']

for (let i = 0; i < arr.length; i += 1) {
  if (i > 1) {
    break
  }
  console.log(arr[i])
}
// 'A'
// 'B'

arr.forEach(async item => {
  await request(item) // forEach는 await 기다려주지않음 (for문은 가능)
})
```

### .includes()

대상 배열이 특정 요소를 포함하고 있는지 확인합니다.

```js
const arr = [1, 2, 3]

console.log(arr.includes(2)) // true
```

```js
const fruits = ['Apple', 'Banana', 'Cherry']

console.log(fruits.includes('Apple')) // true
console.log(fruits.includes('cherry')) // false
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]
console.log(users.includes({ name: 'Neo', age: 85 })) // false

const neo = users[0]
console.log(users.includes(neo)) // true
```

### .join()

대상 배열의 모든 요소를 구분자로 연결한 문자를 반환합니다.

```js
const fruits = ['Apple', 'Banana', 'Cherry']

console.log(fruits.join()) // 'Apple,Banana,Cherry'
console.log(fruits.join(', ')) // 'Apple, Banana, Cherry'
console.log(fruits.join('/')) // 'Apple/Banana/Cherry'
```

### .map()

대상 배열의 길이만큼 주어진 콜백을 실행하고,  
콜백의 반환 값을 모아 새로운 배열을 반환합니다.

```js
const numbers = [1, 2, 3, 4]
const newNumbers = numbers.map(item => item * 2)

console.log(newNumbers) // [2, 4, 6, 8]
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]
const newUsers = users.map(user => ({
  ...user,
  isValid: true,
  email: null
}))

console.log(newUsers)
```

### .pop()

대상 배열에서 마지막 요소를 제거하고 그 요소를 반환합니다.  
대상 배열 원본이 변경됩니다.

```js
const fruits = ['Apple', 'Banana', 'Cherry']

console.log(fruits.pop()) // 'Cherry'
console.log(fruits) // ['Apple', 'Banana']
```

### .push()

대상 배열의 마지막에 하나 이상의 요소를 추가하고, 배열의 새로운 길이를 반환합니다.  
대상 배열 원본이 변경됩니다.

```js
const fruits = ['Apple', 'Banana', 'Cherry']

const newLength = fruits.push('Orange')
console.log(newLength) // 4
console.log(fruits) // ['Apple', 'Banana', 'Cherry', 'Orange']

fruits.push('Mango', 'Strawberry')
console.log(fruits)
// ['Apple', 'Banana', 'Cherry', 'Orange', 'Mango', 'Strawberry']
```

### .reduce()

대상 배열의 길이만큼 주어진 콜백을 실행하고, 마지막에 호출되는 콜백의 반환 값을 반환합니다.  
각 콜백의 반환 값은 다음 콜백으로 전달됩니다.

```js
const numbers = [1, 2, 3]

// const result = numbers.reduce((acc, cur) => acc + cur, 0)
const result = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue
}, 0)

console.log(result) // 6
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]

// 총 나이 계산
const totalAge = users.reduce((acc, cur) => acc + cur.age, 0)
console.log(totalAge) // 118
console.log(`평균 나이: ${(totalAge / users.length).toFixed(1)}세`) // '평균 나이: 39.3세'

// 모든 이름 추출
const names = users
  .reduce((acc, cur) => {
    acc.push(cur.name)
    return acc
  }, [])
  .join(', ')
console.log(names) // 'Neo, Amy, Lewis'
```

### .reverse()

대상 배열의 순서를 반전합니다.  
대상 배열 원본이 변경됩니다.

```js
const arr = ['A', 'B', 'C']
const reversed = arr.reverse()

console.log(reversed) // ['C', 'B', 'A']
console.log(arr) // ['C', 'B', 'A']
```

```js
const str = 'Hello~'
const reversedStr = str.split('').reverse().join('')

console.log(reversedStr) // '~olleH'
console.log(str) // 'Hello~'
```

### .shift()

대상 배열에서 첫 번째 요소를 제거하고, 제거된 요소를 반환합니다.  
대상 배열 원본이 변경됩니다.

```js
const arr = ['A', 'B', 'C']

console.log(arr.shift()) // 'A'
console.log(arr) // ['B', 'C']
```

### .slice()

대상 배열의 일부를 추출해 새로운 배열을 반환합니다.  
두 번째 인수 직전까지 추출하고, 두 번째 인수를 생략하면 대상 배열의 끝까지 추출합니다.

```js
const arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

console.log(arr.slice(0, 3)) // ['A', 'B', 'C']
console.log(arr.slice(4, -1)) // ['E', 'F']
console.log(arr.slice(4)) // ['E', 'F', 'G'] 
console.log(arr) // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
```

### .some()

대상 배열의 어떤 요소라도 콜백 테스트를 통과하는지 확인합니다.

```js
const arr = [1, 2, 3, 4]
const isValid = arr.some(item => item > 3)

console.log(isValid) // true
```

### .sort()

대상 배열을 콜백의 반환 값에 따라 정렬합니다.  
콜백을 제공하지 않으면, 요소를 문자열로 변환하고 유니코드 코드 포인트 순서로 정렬합니다.  
대상 배열 원본이 변경됩니다.

**콜백의 반환 값:**
- 음수: `a`를 낮은 순서로 정렬
- `0`: 순서 변경 없음
- 양수: `b`를 낮은 순서로 정렬

```js
const numbers = [4, 17, 2, 103, 3, 1, 0]

numbers.sort()
console.log(numbers) // [0, 1, 103, 17, 2, 3, 4]

numbers.sort((a, b) => a - b)
console.log(numbers) // [0, 1, 2, 3, 4, 17, 103]

numbers.sort((a, b) => b - a)
console.log(numbers) // [103, 17, 4, 3, 2, 1, 0]
```

```js
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 }
]

users.sort((a, b) => a.age - b.age)
console.log(users) // [ Lewis객체, Amy객체, Neo객체 ]

// users.sort((a, b) => b.age - a.age)
// console.log(users) // [ Neo객체, Amy객체, Lewis객체 ]
```

### .splice()

대상 배열에 요소를 추가하거나 삭제하거나 교체합니다.  
대상 배열 원본이 변경됩니다.

요소 추가

```js
const arr = ['A', 'B', 'C']
arr.splice(2, 0, 'X')

console.log(arr) // ['A', 'B', 'X', 'C']
```

요소 삭제

```js
const arr = ['A', 'B', 'C']
arr.splice(1, 1)

console.log(arr) // ['A', 'C']
```

요소 교체

```js
const arr = ['A', 'B', 'C']
arr.splice(1, 1, 'X')

console.log(arr) // ['A', 'X', 'C']
```

요소 추가 및 삭제

```js
const arr = ['A', 'B', 'C']
arr.splice(0, 0, 'X', 'Y', 'Z')

console.log(arr) // ['X', 'Y', 'Z', 'A', 'B', 'C']
```

### .unshift()

새로운 요소를 대상 배열의 맨 앞에 추가하고 새로운 배열의 길이를 반환합니다.
대상 배열 원본이 변경됩니다.

```js
const arr = ['A', 'B', 'C']

console.log(arr.unshift('X')) // 4
console.log(arr) // ['X', 'A', 'B', 'C']
```

### Array.from()

유사 배열(Array-like)을 실제 배열로 반환합니다.

```js
const arraylike = {
  0: 'A',
  1: 'B',
  2: 'C',
  length: 3
}

console.log(arraylike.constructor === Array) // false
console.log(arraylike.constructor === Object) // true

// arraylike.forEach(item => console.log(item)) // Error!
Array.from(arraylike).forEach(item => console.log(item))
// 'A'
// 'B'
// 'C'
```

### Array.isArray()

배열 데이터인지 확인합니다.

```js
const array = ['A', 'B', 'C']
const arraylike = {
  0: 'A',
  1: 'B',
  2: 'C',
  length: 3
}

console.log(Array.isArray(array)) // true
console.log(Array.isArray(arraylike)) // false
```

