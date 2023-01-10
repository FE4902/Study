## 1. 변수

#### var

-   한번 선언된 변수를 다시 선언할 수 있다
-   선언하기 전에 사용할 수 있다
-   생성과정: 선언 및 초기화 > 할당
-   함수 스코프

> 호이스팅 :<br/>
> 스코프 내부 어디서든 변수 선언은 최상위에 선언된 것 처럼 행동

#### let, const

-   생성과정: 선언 > 초기화 > 할당 (선언과 초기화가 분리됨)
-   TDZ(Temporal Dead Zone)의 영향을 받아 선언하기 전에 사용할 수 없음
-   블록 스코프

> var는 이제 사용하지 않고 let, const 사용을 권장함

## 2. 생성자 함수

-   첫번째 문자는 대문자로 하는것이 관례
-   new 연산자를 사용해서 호출

```javascript
function User(name, age) {
    this.name = name;
    this.age = age;
}

let user5 = new User("Han", 40);
```

## 3. 객체 메소드

#### Object.assign() : 객체 복제

```javascript
const user = {
    name: "Mike",
    age: 30,
};

Object.assign({ gender: "male" }, user);

// 3개 이상도 가능
const user = {
    name: "Mike",
};
const info1 = {
    age: 30,
};
const info2 = {
    gender: "male",
};

Object.assign(user, info1, info2);
```

#### Object.keys() : 키 배열 반환

```javascript
const user = {
    name: "Mike",
    age: 30,
    gender: "male",
};

Object.keys(user);
//["name", "age", "gender"]
```

#### Object.values() : 값 배열 반환

```javascript
const user = {
    name: "Mike",
    age: 30,
    gender: "male",
};

Object.values(user);
//["Mike", 30, "male"]
```

#### Object.entries() : 키/값 배열 반환

```javascript
const user = {
    name: "Mike",
    age: 30,
    gender: "male",
};

Object.entries(user);
// [
//     ["name", "Mike"],
//     ["age", 30],
//     ["gender", "male"],
// ];
```

## 4. 심볼

-   유일성 보장

```javascript
const a = Symbol("id"); // new를 붙이지 않음
const b = Symbol("id");

a == b; // false
```

#### Symbol.for() : 전역 심볼

```javascript
const a = Symbol.for("id");
const b = Symbol.for("id");

a == b; // true
```

#### keyFor, description : 키 값 가져오기

```javascript
const a = Symbol.for("id");
const b = Symbol("id");

Symbol.keyFor(a); // 전역심볼일 때 키 값 가져오기
a.description; // 전역심볼이 아닌경우 키 값 가져오기
```

#### getOwnPropertySymbols, ownKeys : 숨겨진 Symbol key 보기

```javascript
const a = Symbol("id");
const user = {
    name: "Mike",
    age: 30,
    [id]: "myId",
};

Object.getOwnPropertySymbols(user); // [Symbol(id)]
Reflect.ownKeys(user); // ['name', 'age', Symbol(id)]
```

## 5. 숫자, 수학

#### toString()

```javascript
let num1 = 10;

num1.toString(); // "10"
num1.toString(2); // "1010"

let num2 = 255;

num2.toString(16); // "ff"
```

#### Math.ceil(), Math.floor(), Math.round()

```javascript
let num1 = 5.1;
let num2 = 5.7;

// Math.ceil() : 올림
Math.ceil(num1); // 6
Math.ceil(num2); // 6

// Math.floor() : 내림
Math.floor(num1); // 5
Math.floor(num2); // 5

// Math.round() : 반올림
Math.round(num1); // 6
Math.round(num2); // 6
```

#### toFixed() : 소수점 자릿수

```javascript
let userRate = 30.1234;

// 문자로 반환
userRate.toFixed(0); // '30'
userRate.toFixed(2); // '30.12'
userRate.toFixed(6); // '30.123400'
```

#### isNaN()

```javascript
let x = Number("x"); // NaN

// boolean으로 반환
isNaN(x); // true
```

#### parseInt()

```javascript
let margin = "10px";

parseInt(margin); // 10
Number(margin); // NaN

let redColor = "f3";
parseInt(redColor); // NaN
parseInt(redColor, 16); // 243
```

#### parseFloat()

```javascript
let padding = "18.5%";

parseInt(padding); // 18
// 부동소수점 반환
parseFloat(padding); // 18.5
```

#### Math.random() : 0 ~ 1 사이 무작위 숫자 생성

```javascript
Math.random(); // 0.23433425789
```

#### Math.max(), Math.min()

```javascript
Math.max(1, 4, -1); // 4
Math.min(1, 4, -1); // -1
```

#### Math.abs() : 절대값

```javascript
Math.abs(-1); // 1
```

#### Math.pow(n, m) : 제곱

```javascript
Math.pow(2. 10); // 1024
```

#### Math.sqrt() : 제곱근

```javascript
Math.sqrt(16); // 4
```
