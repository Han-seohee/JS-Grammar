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

---
2021.09.06
### :dog:Truthy and Falsy

>Truthy

```
function print(person) {
 if (person === undefined) {
  return;
 }
 console.log(person.name);
}

const person = {
 name: 'John'
};

print();
```

```
function print(person) {
 if (person === undefined || person === null) {
  return;
 }
 console.log(person.name);
}

const person = null

print(person);
```

```
function print(person) {
 if (!person) {
  return;
 }
 console.log(person.name);
}

const person = null

print(person);
```

```
console.log(!undefined);
console.log(!null);
console.log(!0);
console.log(!'');
console.log(!NaN);
console.log(!false);

// true
   true
   true
   true
   true
   true
```

>Falsy : Truthy 를 제외한 모든 값

```
console.log(!3);
console.log(!'hello');
console.log(!['array']);
console.log(![]);
console.log(!{});

// false
   false
   false
   false
   false
```

---
2021.09.07
### :dog:단축 평가 논리 계산법

>&&연산자
>>특정 값이 유효 할 때만 어떤 값을 조회 해야 하는 상황에 사용

```
const dog = {
 name: '멍멍이'
};

function getName(animal) {
 if (animal) {
  return animal.name;
 }
 return undefined;
}

const name = getName();
console.log(name);
```

:point_down:

```
const dog = {
 name: '멍멍이'
};

function getName(animal) {
 return animal && animal.name;
}

const name = getName();
console.log(name);
```

>&&연산자
>>앞에 오는 것이 true or trythy 이면 결과는 오른쪽에 있는 값
>>앞에 오는 것이 falsy 이면 결과는 앞에 있는 값

```
console.log(true && 'hello'); // hello
console.log(false && 'hello'); // false
console.log('hello && 'bye'); // bye
console.log(null && 'hello'); // null
console.log(undefined && 'hello'); // undefined
console.log('' && 'hello'); // ''
console.log(0 && 'hello'); // 0
console.log(1 && 'hello'); // hello
console.log(1 && 1); // 1
```

>|| 연산자

```
const namelessDog = {
 name: '',
};

function getName(animal) {
 const name = animal && animal.name;
 if (!name) {
  return '이름이 없는 동물입니다.';
 }
 return name;
}

const name = getName(nameleeDog);
console.log(name);

// 이름이 없는 동물입니다.
```

:point_down:

```
const namelessDog = {
 name: '',
};

function getName(animal) {
 const name = animal && animal.name;
 return name || '이름이 없는 동물입니다.';
}

const name = getName(nameleeDog);
console.log(name);

// 이름이 없는 동물입니다.
```

또는

```
const namelessDog = {
 name: '뭉뭉이',
};

function getName(animal) {
 const name = animal && animal.name;
 return name || '이름이 없는 동물입니다.';
}

const name = getName(nameleeDog);
console.log(name);

// 뭉뭉이
```

>||연산자
>>앞에 오는 것이 falsy 이면 결과는 오른쪽에 있는 값
>>앞에 오는 것이 true or trutyh 이면 앞에 있는 값

```
console.log(false || 'hello'); // hello
console.log('' || '이름없다'); // 이름없다
console.log(null || '널이다~'); // 널이다~
console.log(undefined || 'defined 되지 않았다!'); // defined 되지 않았다!
console.log(0 || '제로다'); // 제로다
```

```
console.log(1 || '음?'); // 1
console.log(true || '여기 안본다.'); // true
console.log('와아' || '여기 안봐요'); // 와아
console.log([] || '노노'); // []
```

