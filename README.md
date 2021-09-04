# JS-Grammar 자바스크립트 문법 
2021.09.04
### :dog:삼항연산자

```
const array = [1, 2];
let text = '';
if (array.length === 0) {
 text = '배열이 비어있습니다.';
 } else {
   text = '배열이 비어있지 않습니다.';
}
console.log(text);

// 값 : 배열이 비어있지 않습니다.
```

:point_down:

```
const array = [1, 2];
let text = array.length === 0 
 ? '배열이 비어있습니다.' 
 : '배열이 비어있지 않습니다.';
console.log(text);

// 값 : 배열이 비어있지 않습니다.
```

>중첩
>>가급적 사용X

```
const condition1 = false;
const condition2 = false;

const value = condition1
 ? '와우!'
 : condition2
  ?'blabla'
  : 'foo'

console.log(value)

// 값 : foo
```
