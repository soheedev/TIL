# ch09-03 변수, 예약어
* `#패스트캠퍼스` `#국비지원교육` `#메가바이트스쿨` `#MegabyteSchool` `#개발자취업부트캠프` `#내일배움카드`
> 패스트캠퍼스 프론트엔드 초격차 패키지

### 변수
* let, var, const

### 변수 선언! 
* (지속적으로 ) 재사용이 가능!
```
let a = 2;
let b = 5;

console.log(a + b); // 7
console.log(a - b); // -3
console.log(a * b); // 10
console.log(a / b); // 0.4
```

### let
* 값(데이터)의 재할당 가능! 
```
let a = 12; 
console.log(a); // 12

a = 999; 
console.log(a); // 999
```
 
### const
* 값(데이터)의 재할당 불가! 
```
const a = 12;
console.log(a); // 12

a = 999; 
console.log(a); // TypeError: Assignment to constant variable.
```

### 예약어 
* 특별한 의미를 가지고 있어, 변수나 함수 이름 등으로 사용할 수 없는 단어 Reserved Word 
* 에디터에서 오류로 표시해줌
```
let this = 'Hello!'; // SyntaxError
let if = 123; // SyntaxError
let break = true; // SyntaxError
 ```

```
break, case, catch, continue, default, delete, do, else, false, fina lly, for, 
function, if, in, instanceof, new, null, return, switch, this, throw, true, try, typeof,
 var, void, while, with, abstract, boolean, byte, char, class, const, debugger, double, 
 enum, export, extends, final, float, goto, implements, import, int, interface, long, native,
package, private, protected, public, shor t, static, super, synchronized, throws, transient,
volatile, as, is, namespace, use, arguments, Array, Boolean, Date, decodeURI, decodeURIComponent,
encodeURI, Error, escape, eval, EvalError, Function, Infinity, isFinite, isNaN, Math, NaN, Number,
Object, parseFloat, parseInt, RangeError, ReferenceError, RegExp, String, SyntaxError, TypeError,
undefined, unescape, URIError ... 
```


