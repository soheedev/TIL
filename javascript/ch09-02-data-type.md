# ch9-02 데이터 종류(자료형)
> 패스트캠퍼스 프론트엔드 초격차 패키지
`#패스트캠퍼스` `#국비지원교육` `#메가바이트스쿨` `#MegabyteSchool` `#개발자취업부트캠프` `#내일배움카드`

### String (문자 데이터)
* 따옴표를 사용, 백틱사용
```
let 변수 =  문자데이터
let myName = “sohee”
let hello = `Hello ${myName}!!` //(보관법) 그레이브 기호(백틱)사용

console.log(myName); // sohee
console.log(hello); // Hello sohee!!
```

### Number(숫자 데이터)
* 정수 및 부동소수점 숫자를 나타냄
```
let number = 1234; // 따옴표를 사용하게 되면 문자데이터가 됨(주의)
let opacity = 1.37;

console.log(number); // 1234
console.log(opacity); // 1.37
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
```
let undef;
let obj = { abc: 123 }; // 객체데이터 - 속성(abc)에 값(123) 할당

console.log(undef); // undefined
console.log(obj.abc); // 123
console.log(obj.xyz); // undefined
```
### Null
* 어떤 값이 의도적으로 비어있음을 의미
```
let empty = null; // 값이 없음을 명시, undefined는 의도하지 않게 값이 할당되지 않은 상태

console.log(empty); // null
```
### Object(객체 데이터)
* 중괄호{ } 사용하여 여러 데이터를 Key:Value 형태로 저장
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
```

### Array(배열 데이터)
* 대괄호[ ] 사용하여 여러 데이터를 순차적으로 저장
```
let fruits = [‘Apple’, ‘Banana’, ‘’Mango, ‘Cherry’];

console.log(fruits[0]); // Apple
console.log(fruits[1]); // Banana
console.log(fruits[2]); // Mango
```

* 자바스크립트 명령문 뒤에 세미콜론(;)을 붙이는게 원칙
* 없어도 자바스크립트엔진이 알아서 세이콜론을 붙여서 해석함


