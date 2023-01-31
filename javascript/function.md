# ch09-04 함수
> 패스트캠퍼스 프론트엔드 초격차 패키지

### 함수 선언
* `매개변수와 인수는 다르기에 구분할 필요가 있다.`
```
function sum(a, b) { // a와 b는 매개변수(Parameters) 
    return a + b; 
} 

// 재사용! 
let a = sum(1, 2); // 1과 2는 인수(Arguments => 곧 데이터) 
let b = sum(7, 12);
let c = sum(2, 4);

console.log(a, b, c); // 3, 19, 6
```

### 함수 선언! 
* 기명(이름이 있는) 함수 
```
function hello() {
    console.log('Hello~');
} 
```

### 함수 표현! 
* 익명(이름이 없는) 함수 
```
let world = function () {
    console.log('World~');
} 
```
* 함수 선언과 함수 표현의 개념에 대해 알아둘것
- 함수안에 'return undefined' 가 생략이 되어 있음
* 호이스팅(Hoisting)관련하여 위 개념아 사용됨

### 함수 호출! 
```
hello(); // Hello~
world(); // World~

//함수 선언 후 호출
function helloFunc() {
   // 실행 코드 
   console.log(1234);
}
helloFunc();// 1234


function returnFunc() {
    return 123; 
} 

let a = returnFunc();
console.log(a); // 123
```

### 객체 데이터 
```
const heropy = {
    name: 'HEROPY',
    age: 85, 

    // 메소드(Method): 속성이 아닌 메소드로 불리움
    getName: function () { // 함수표현
        return this.name; // this: 본인이 소속되어 있는 객체 데이터를 의미
    } 
};
```
* 객체 데이터 안에 속성이 함수일때 더이상 속성이 아닌 메소드라고 불리움
```
const hisName = heropy.getName(); // 함수 호출(실행)
console.log(hisName); // HEROPY
// 혹은 
console.log(heropy.getName()); // HEROPY
```
