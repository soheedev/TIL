# 표준 내장 객체
* `#패스트캠퍼스` `#국비지원교육` `#메가바이트스쿨` `#MegabyteSchool` `#개발자취업부트캠프` `#내일배움카드`

## Object

### Object.assign()

하나 이상의 출처(Source) 객체로부터 대상(Target) 객체로 속성을 복사하고 대상 객체를 반환합니다.

```js
const target = { a: 1, b: 2 }
const source1 = { b: 3, c: 4 }
const source2 = { c: 5, d: 6 }
const result = Object.assign(target, source1, source2)

console.log(target) // { a: 1, b: 3, c: 5, d: 6 }
console.log(result) // { a: 1, b: 3, c: 5, d: 6 }
```

새로운 객체를 반환하려면, 빈 객체를 대상으로 추가할 수 있습니다.

```js
const target = { a: 1, b: 2 }
const source1 = { b: 3, c: 4 }
const source2 = { c: 5, d: 6 }
const result = Object.assign({}, target, source1, source2)

console.log(target) // { a: 1, b: 2 }
console.log(result) // { a: 1, b: 3, c: 5, d: 6 }
```

전개 연산자를 사용할 수도 있습니다.

```js
const target = { a: 1, b: 2 }
const source1 = { b: 3, c: 4 }
const source2 = { c: 5, d: 6 }
const result = {
  ...target,
  ...source1,
  ...source2
}

console.log(target) // { a: 1, b: 2 }
console.log(result) // { a: 1, b: 3, c: 5, d: 6 }
```

### Object.entries()

주어진 객체의 각 속성과 값으로 하나의 배열 만들어 요소로 추가한 2차원 배열을 반환합니다.

```js
const user = {
  name: 'Heropy',
  age: 85,
  isValid: true,
  email: 'thesecon@gmail.com'
}

console.log(Object.entries(user))
// [
//   ['name', 'Heropy'], 
//   ['age', 85], 
//   ['isValid', true], 
//   ['email', 'thesecon@gmail.com']
// ]

for (const [key, value] of Object.entries(user)) {
  console.log(key, value)
}
// name Heropy
// age 85
// isValid true
// email thesecon@gmail.com
```

### Object.keys()

주어진 객체의 속성 이름을 나열한 배열을 반환합니다.

```js
const user = {
  name: 'Heropy',
  age: 85,
  isValid: true,
  email: 'thesecon@gmail.com'
}

console.log(Object.keys(user)) // ['name', 'age', 'isValid', 'email']
```

### Object.values()

주어진 객체의 속성 값을 나열한 배열을 반환합니다.

```js
const user = {
  name: 'Heropy',
  age: 85,
  isValid: true,
  email: 'thesecon@gmail.com'
}

console.log(Object.values(user))
// ['Heropy', 85, true, 'thesecon@gmail.com']
```

### Object.freeze()와 Object.isFrozen()

주어진 객체를 변경할 수 없도록 동결하거나, 동결 여부를 확인합니다.

```js
const user = {
  name: 'Heropy',
  age: 85
}

user.age = 44
console.log(user) // { name: 'Heropy', age: 44 }
console.log(Object.isFrozen(user)) // false

// 동결!
Object.freeze(user)

user.age = 22
user.email = 'thesecon@gmail.com'
console.log(user) // { name: 'Heropy', age: 44 }
console.log(Object.isFrozen(user)) // true
```

### Object.seal()과 Object.isSealed()

주어진 객체를 변경할 수 없도록 밀봉하거나, 밀봉 여부를 확인합니다.  
동결과 다른 점은 밀봉 후에도 속성의 값을 변경할 수 있습니다.

```js
const user = {
  name: 'Heropy',
  age: 85
}

user.age = 44
console.log(user) // { name: 'Heropy', age: 44 }
console.log(Object.isSealed(user)) // false

// 밀봉!
Object.seal(user)

user.age = 22 // 변경 가능!
user.email = 'thesecon@gmail.com'
console.log(user) // { name: 'Heropy', age: 22 } // 변경됨!
console.log(Object.isSealed(user)) // true
```

### Object.defineProperty()

주어진 객체에 속성을 추가하거나, 특성을 변경합니다.

`속성: 기본값` | 설명
---|---
`enumerable: false` | 속성의 열거 가능 여부
`configurable: false` | 속성의 수정(이미 존재할 때), 삭제 가능 여부
`writable: false` | 속성의 값 변경 가능 여부
`value: undefined` | 속성의 값
`get: undefined` | 속성의 Getter
`set: undefined` | 속성의 Setter

```js
const user = {}
Object.defineProperty(user, 'name', {
  value: 'Heropy'
})
console.log(user.name) // 'Heropy'

// 열거 불가!
for (const key in user) {
  console.log('key:', key) // 출력 없음!
}

// 수정 불가!
user.name = 'Neo'
console.log(user.name) // 'Heropy'

// 삭제 불가!
delete user.name
console.log(user.name) // 'Heropy'
```

```js
const user = {}
Object.defineProperty(user, 'name', {
  value: 'Heropy',
  configurable: true,
  writable: true,
  enumerable: true
})
console.log(user.name) // 'Heropy'

// 열거 불가!
for (const key in user) {
  console.log(key) // 'name'
}

// 수정 불가!
user.name = 'Neo'
console.log(user.name) // 'Neo'

// 삭제 불가!
delete user.name
console.log(user.name) // undefined
```

```js
const user = {
  _name: 'Heropy'
}
Object.defineProperty(user, 'name', {
  get() {
    return this._name
  },
  set(value) {
    this._name = value
    console.log(`이름이 ${value}로 바뀌었습니다!`)
  }
})

// Get!
console.log(user.name) // 'Heropy'

// Set!
user.name = 'Neo' // '이름이 Neo로 바뀌었습니다!'

for (let key in user) {
  console.log(key) // '_name'
}
```

### Object.defineProperties()

주어진 객체에 여러 속성을 추가하거나, 특성을 변경합니다.

```js
const user = {}
Object.defineProperties(user, {
  name: {
    enumerable: true,
    value: 'Heropy'
  },
  age: {
    enumerable: true,
    value: 85
  },
  email: {
    enumerable: true,
    configurable: true,
    writable: true,
    value: []
  },
  address: {
    value: '경기 수원시'
  }
})

console.log(user)
for (const key in user) {
  console.log(key)
}
// 'name'
// 'age'
// 'email'
```

