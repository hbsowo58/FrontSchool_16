# Destructuring

spread 연산자가 아니다(연산자란, 피연산자를 바탕으로 새로운 값을 만들어내야함) 새로운 값을 만들어내진 않음

<br>

디스트럭처링 할당(구조 분해 할당, Destructuring assignment)은 구조화된 배열 또는 객체를 Destructuring(비구조화, 구조파괴)하여 1개 이상의 변수에 개별적으로 할당하는 것을 말한다. 배열 또는 객체 리터럴에서 필요한 값만을 추출하여 변수에 할당할 때 유용하다.

->사용처는 객체나 배열같은 자료구조에서 변수에 '개별' 할당할때

<br>

### 배열 디스트럭처링 할당

```javascript
const arr = [1, 2, 3];

// ES6 배열 디스트럭처링 할당
// 변수 one, two, three를 선언하고 배열 arr을 디스트럭처링하여 할당한다.
// 이때 할당 기준은 배열의 인덱스이다.
const [one, two, three] = arr;

console.log(one, two, three); // 1 2 3
//배열 디스트럭처링 할당을 위해서 할당 연산자의 왼쪽에 값을 할당 받을 변수를 선언해야하고 배열 리터럴 형태로 선언

let x;
let y;
[x,y] = [1,2];
//위아래 동치
const [x, y] = [1, 2];

```

여러 개의 변수를 배열 형태로 선언하면 반드시 우변에 배열을 할당해야 한다.

```javascript
let x, y, z; //let은 되는데 const는 안된다. 초기값을 줘야하는데 여러개를 한번에 못준다(???)

[x, y] = [1, 2];
console.log(x, y); // 1 2

[x, y] = [1];
console.log(x, y); // 1 undefined

[x, a] = [1];
console.log(x, y); // 1 undefined 암묵적으로 var를 만든다

[x, y] = [1, 2, 3];
console.log(x, y); // 1 2

[x, , z] = [1, 2, 3];
console.log(x, z); // 1 3

//선언과 할당을 분리하면 암묵적인 문제가 발생할 수 있으니 분리하지말자
```

```javascript
const today = new Date(); // 현업에서 사용x 라이브러리를 사용해서 사람이 읽을 수 있는 형식을 사용
console.log(today); // Sun Mar 22 2020 22:00:55 GMT+0900 (대한민국 표준시)

const formattedDate = today.toISOString().substring(0, 10);
console.log(formattedDate); // "2020-03-22"

// 문자열을 분리하여 배열로 변환한 후, 배열 디스트럭처링 할당을 통해 필요한 요소를 취득한다.
const [year, month, day] = formattedDate.split('-');
console.log([year, month, day]); // ["2020", "03", "22"]
```

## 객체  (디스트럭처링 할당 활용도 ↑)

ES5에서 객체의 각 프로퍼티를 객체로부터 디스트럭처링하여 변수에 할당하기 위해서는 프로퍼티 키를 사용해야 한다.

<br>

ES6의 객체 디스트럭처링 할당은 객체의 각 프로퍼티를 객체로부터 추출하여 1개 이상의 변수에 할당한다. 배열 디스트럭처링 할당과 마찬가지로 객체 디스트럭처링 할당을 위해서는 할당 연산자 왼쪽에 값을 할당 받을 변수를 선언해야 한다.

이를 위해 여러 개의 변수를 객체 리터럴 형태로 선언한다. 이때 할당 기준은 프로퍼티 키이다. 즉, 순서는 의미가 없으며 변수 이름과 프로퍼티 키가 일치하면 할당된다.

```javascript
const user = { firstName: 'BEOMSUNG', lastName: 'HEO' };

// ES6 객체 디스트럭처링 할당
// 프로퍼티 키를 기준으로 디스트럭처링 할당이 이루어진다.
// 프로퍼티 키가 lastName인 프로퍼티 값을 ln에 할당한다.
// 프로퍼티 키가 firstName인 프로퍼티 값을 fn에 할당한다.
const { lastName: ln, firstName: fn } = user; //비추

console.log(fn, ln); // BEOMSUNG HEO
```

```javascript
const todo = { id: 1, content: 'HTML', completed: true };

// todo 객체로부터 id 프로퍼티만을 추출한다.
const { id } = todo;
console.log(id); // 1
```

객체 디스트럭처링 할당을 위한 변수에 Rest 파라미터와 유사하게 Rest 프로퍼티 …을 사용할 수 있다. Rest 프로퍼티는 Rest 파라미터와 마찬가지로 반드시 마지막에 위치해야 한다.

```javascript
// Rest 프로퍼티
const { x, ...rest } = { x: 1, y: 2, z: 3 };
console.log(x, rest); // 1 { y: 2, z: 3 }
```

