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

---
2021.09.09
### :dog:함수의 기본 파라미터
>함수로 호출시 원래 넣어야 할 파라미터를 넣지 않게 됐을 때 기본값으로 사용할 값을 지정하는것

+ 원의 넓이를 구하는 함수

```
function calculateCircleArea(r) {
 return Math.PI * r * r;
}

const area = calculateCircleArea(4);
console.log(area)

// 50.26548245743669
```

>4를 넣지 않는다면

```
function calculateCircleArea(r) {
 feturn Math.PI * r * r;
}

const area = calculateCircleArea();
console.log(area)

// NaN
```

>파라미터를 넣어야하는데 안넣었을 때 어떤 값을 기본값으로 사용하고 싶을 때
>>단축 평가 논리 계산법

```
function calculateCircleArea(r) {
 const radius = r || 1;
 return Math.PI * radius * radius;
}

const area = calculateCircleArea();
console.log(area)

//  3.141592653589793
```

>ES6 함수 기본 파라미터 문법

```
function calculateCircleArea(r = 1) {   // 1을 기본값으로 사용
 return Math.PI * r* r;
}

const area = calculateCircleArea();
console.log(area)

//  3.141592653589793
```

>화살표 함수
```
const calculateCircleArea = (r = 1) => Math.PI * r* r;

const area = calculateCircleArea();
console.log(area)

//  3.141592653589793
```

---
### :dog:조건문 더 스마트하게 쓰기
+ 특정 값이 여러 값 중에 하나인지 확인하기

```
function isAnimal(text) {
 return (
  text === '고양이' || text === '개' || text === '거북이' || text === '너구리'
 );
}

console.log(isAnimal('개'));
console.log(isAnimal('노트북'));

// true
   false (노트북은 없으니까)
```

:point_down:비교하고 싶은것을 배열안에 넣는다

```
function isAnimal(text) {
 const animals = ['고양이', '개', '거북이', '너구리'];
 return animals.includes(text);
}

console.log(isAnimal('개'));
console.log(isAnimal('노트북'));

// true
   false (노트북은 없으니까)
```

:point_down:화살표함수

```
const isAnimal = text => ['고양이', '개', '거북이', '너구리'].includes(text);

console.log(isAnimal('개'));
console.log(isAnimal('노트북'));

// true
   false (노트북은 없으니까)
```

+주어진 값에 따라 다른 결과물을 반환해야 할 때

```
function getSound(animal) {
 if (animal === '개') return '멍멍!';       // if 문이 한 줄이면 블록 생략 가능
 if (animal === '고양이') return '야옹-';
 if (animal === '참새') return '짹짹';
 if (animal === '비둘기') return '구구 구 구';
 return '...?';
}

console.log(getSound('개'));
console.log(getSound('비둘기'));
console.log(getSound('인간'));

// 멍멍!
   구구 구 구
   ...?
```

:point_down: switch case (추천x)

```
function getSound(animal) { //switch case 안에서 return을 하게 된다면 굳이 break 할 필요 없음
 switch (animal) {
  case '개':
   return '멍멍!';
  case '고양이':
   return '야옹-';
  case '참새':
   return '짹짹';
  case '비둘기':
   return '구구 구 구!';
  default:
   return '...?'
  }
}

console.log(getSound('개'));
console.log(getSound('비둘기'));
console.log(getSound('인간'));

// 멍멍!
   구구 구 구!
   ...?
```

:point_down: 객체 활용 (깔끔:o: 추천:o:)
>어떤 값을 넣느냐에 따라 반환하는 값이 달라지는 경우

```
function getSound(animal) {
 const sounds = {
  개: '멍멍!',
  고양이: '야옹-',
  참새: '짹짹',
  비둘기: '구구 구 구'
 };
 return sounds[animal] || '...?';
}

console.log(getSound('개'));
console.log(getSound('비둘기'));
console.log(getSound('인간'));

// 멍멍!
   구구 구 구!
   ...?
```

:point_down:특정 값이 무엇으로 주어지느냐에 따라서 다른 코드를 실행하고 싶을 때

```
function makeSound(animal) {
 const tasks = {
  개: () => {
   console.log('멍멍!');
  },
  고양이: () {
   console.log('야옹!');
  },
  비둘기: function()  {     // 추천X
   console.log('구구 구 구');
  }
 }

 const task = tasks[animal];
 if (!tasks) {
  console.log('...?');
  return;
 }
 tasks[animal]();
}

makeSound('개');
makeSound('비둘기');
makeSound('인간');

// 멍멍!
   구구 구 구
   ...?
```
