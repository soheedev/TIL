# ch9-02 데이터 종류(자료형)
> 패스트캠퍼스 프론트엔드 초격차 패키지

## 원시형 데이터

### String (문자 데이터)
* 따옴표를 사용, 백틱사용(템플릿 리터럴)
* 리터럴: 기호(",',`,{},[] 등)를 통해서 데이터를 만드는 것
```
let 변수 =  문자데이터
let myName = “sohee”
let hello = `Hello ${myName}!!` //(보간법) 그레이브 기호(백틱)사용

console.log(myName); // sohee
console.log(hello); // Hello sohee!!
```

### Number(숫자 데이터)
* 정수(integer) 및 부동소수점(float) 숫자를 나타냄
```
let number = 1234; // 따옴표를 사용하게 되면 문자데이터가 됨(주의)
let opacity = 1.37;
const aaa  = .1;

console.log(number); // 1234
console.log(opacity); // 1.37
console.log(aaa); //.1
```

* 숫자가 아닌 숫자(Not a Number)
* 숫자이지만 표현이 안되는 숫자(주의)
```
console.log(2 * undefined); //NaN

const str = '123'
console.log(Number(str)) //123

const strNa = 'Hello'
console.log(Number(strNaN))// NaN

console.log(01. + 0.2)// 0.300000000004 부동 소수점 오류
console.log(Number((0.1 + 0.2).toFixed(1))) // 소수점 자리를 한자리수만 남기고 나머지를 버림(문자데이터가 됨)

const a = 3.141592
console.log(a.toFixed(2).slice(0,2)) // 3.

```

### Boolean (불린 데이터)
* true, false 두 가지 값밖에 없는 논리 데이터
```
let checked = true;
let isShow = false;

console.log(checked); // true
console.log(isShow); // false
```

### Undefined 
* 값이 할당되지 않는 상태
* 암시적인 값
```
let undef;
let obj = { abc: 123 }; // 객체데이터 - 속성(abc)에 값(123) 할당

console.log(undef); // undefined
console.log(obj.abc); // 123
console.log(obj.xyz); // undefined
```
### Null
* 어떤 값이 의도적으로 비어있음을 의미
* 명시적인 값
```
let empty = null; // 값이 없음을 명시, undefined는 의도하지 않게 값이 할당되지 않은 상태

console.log(empty); // null
```

### 심볼(Symbol)
- 심볼은 변경이 불가한 데이터
- 유일한 식별자를 만들어 데이터를 보호하는 용도로 사용
- 심볼에 추가하는 '설명'은 디버깅의 용도일 뿐, 심볼 값과는 관계가 없음

```
const sKey = Symbol('Hello')
const user = {
  key: '일반 정보',
 [sKey]: '민감한 정보'
}

console.log(user.key) // '일반정보'
console.log(user[key]) // '일반정보'
console.log(user[sKey]) // '민감한 정보'
console.log(user[Symbol('Hello!')]) // undefined
```

### BigInt
- 길이 제한이 없는 정수


* 자바스크립트 명령문 뒤에 세미콜론(;)을 붙이는게 원칙
* 없어도 자바스크립트엔진이 알아서 세이콜론을 붙여서 해석함
- 할당('='): 변수에 값을 할당
- 동등연산자('=='): 왼쪽 피연산자와 오른쪽 피연산자와 비교
- 일치연산자('==='): 피연사자끼리 타입까지 비교==> `데이터의 메모리 주소를 비교한다`

## 참조형 데이터

### Array (배열 데이터)
* 대괄호[ ] 사용하여 여러 데이터를 순차적으로 저장
- 순서가 있음
- [] 안의 element 또는 item 이라고 함
- 대괄호 표기법: '배열변수명[]' 
- 인덱싱방법: '배열[인덱스번호]' 이런 식으로 접근

```
let fruits = [‘Apple’, ‘Banana’, ‘’Mango, ‘Cherry’];

console.log(fruits[0]); // Apple
console.log(fruits[1]); // Banana
console.log(fruits[2]); // Mango
```

- 배열의 마지막 인덱스접근
```
console.log(fruits[fruits.length - 1])
console.log(fruits.at(-2))
```

### Object (객체 데이터)
* 중괄호{ } 사용하여 여러 데이터를 Key:Value 형태로 저장
- 순서 상관없음
- key(속성)의 이름은 고유해야 함, 중복시 마지막 속성값이 나옴
- 속성, 멤버, 메소드(함수의 경우)라고 불리움

```
let user = {
    // Key: Value,
    name: ‘sohee’,
    age: 80,
    isValid: true
};

console.log(user.name); // sohee
console.log(user.age); // 80
console.log(user.isValied); // true
console.log(user['name']) // sohee
console.log(user['age']) // 80

```


