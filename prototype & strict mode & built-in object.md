# 0508 prototype & strict mode & built-in object

프로토타입 메서드는 인스턴스로 호출한다

Person.prototype.sayHi();식으로 호출x

<br>

모든 객체의 프로퍼티는 public 하다



## 오버라이딩과 프로퍼티 쉐도잉

```javascript
const Person = (function () {
  // 생성자 함수
  function Person(name) {
    this.name = name;
  }

  // 프로토타입 메소드
  Person.prototype.sayHello = function () {
    console.log(`Hi! My name is ${this.name}`);
  };

  // 생성자 함수를 반환
  return Person;
}());

const me = new Person('Lee');

// 인스턴스 메소드
me.sayHello = function () {
  console.log(`Hey! My name is ${this.name}`);
};

// 인스턴스 메소드가 호출된다. 프로토타입 메소드는 인스턴스 메소드에 의해 가려진다.
me.sayHello(); // Hey! My name is Lee
```

me.sayHello() 호출시, 인스턴스 메소드부터 찾아서 실행한다(체인상 가까운쪽부터 실행)

Person.prototype은 프로퍼티 쉐도잉되었고, me는 오버라이딩 하였다

>오버라이딩(overriding)
>
>상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의하여 사용하는 방식이다.



## 프로토타입의 교체

```javascript
//생성자함수.prototype을 이용한 교체방법
const Person = (function () {
  function Person(name) {
    this.name = name;
  }

  // ① 생성자 함수의 prototype 프로퍼티를 통해 프로토타입을 교체
  Person.prototype = {
    sayHello() {
      console.log(`Hi! My name is ${this.name}`);
    }
  };

  return Person;
}());

const me = new Person('Lee');
```

```javascript
//인스턴스.__proto__를 이용한방법
function Person(name) {
  this.name = name;
}

const me = new Person('Lee');

// 프로토타입으로 교체할 객체
const parent = {
  sayHello() {
    console.log(`Hi! My name is ${this.name}`);
  }
};

// ① me 객체의 프로토타입을 parent 객체로 교체한다.
Object.setPrototypeOf(me, parent);
// 위 코드는 아래의 코드와 동일하게 동작한다.
// me.__proto__ = parent;

me.sayHello(); // Hi! My name is Lee


```

두 방법 비추천.



Object.create를 사용해서 직접상속



## instanceof 연산자

**우변의 생성자 함수의 prototype에 바인딩된 객체가 좌변의 객체의 프로토타입 체인 상에 존재하면 true로 평가되고 그렇지 않은 경우에는 false로 평가된다.**

```javascript
//사용법
객체 instanceof 생성자 함수

// 생성자 함수
function Person(name) {
  this.name = name;
}

const me = new Person('Lee');

// Person.prototype이 me 객체의 프로토타입 체인 상에 존재하므로 true로 평가된다.
console.log(me instanceof Person); // true

// Object.prototype이 me 객체의 프로토타입 체인 상에 존재하므로 true로 평가된다.
console.log(me instanceof Object); // true

//아버지의 자식이면서 할아버지의 자식이다 이외에는 모두 false
```

생성자함수.prototype 링크가 깨지면, instanceof에서 문제가 발생한다

![image-20200508155519335](C:\Users\82109\AppData\Roaming\Typora\typora-user-images\image-20200508155519335.png)

person.prototype에 constructor가 존재하지 않지만 체인상 존재하므로 instanceof 연산자를 사용하면

true가 나옴 me instanceof Person



## 직접 상속

Object.create에 의한 직접 상속

```javascript
/**
 * 지정된 프로토타입 및 프로퍼티를 갖는 새로운 객체를 생성하여 반환한다.
 * @param {Object} prototype - 생성할 객체의 프로토타입으로 지정할 객체
 * @param {Object} [propertiesObject] - 생성할 객체의 프로퍼티를 갖는 객체
 * @returns {Object} 지정된 프로토타입 및 프로퍼티를 갖는 새로운 객체
 */
Object.create(prototype[, propertiesObject])
객체를 생성한다(프로토타입을 정하면서, 옵션)
```

객체 리터럴 내부에서 `__proto__` 의한 직접상속



## 정적프로퍼티/메서드

정적(static) 프로퍼티/메소드는 생성자 함수로 인스턴스를 생성하지 않아도 참조/호출할 수 있는 프로퍼티/메소드를 말한다.

```javascript
// 생성자 함수
function Person(name) {
  this.name = name;
}

// 프로토타입 메소드
Person.prototype.sayHello = function () {
  console.log(`Hi! My name is ${this.name}`);
};

// Person 생성자 함수는 객체이므로 자신의 프로퍼티/메소드를 소유할 수 있다.
// 정적 프로퍼티
Person.staticProp = 'static prop';
// 정적 메소드
Person.staticMethod = function () {
  console.log('staticMethod');
};

const me = new Person('Lee');

// 생성자 함수에 추가한 정적 프로퍼티/메소드는 생성자 함수로 참조/호출한다.
Person.staticMethod(); // staticMethod

// 정적 프로퍼티/메소드는 생성자 함수가 생성한 인스턴스로 참조/호출할 수 없다.
// 인스턴스로 참조/호출할 수 있는 프로퍼티/메소드는 프로토타입 체인 상에 존재해야 한다.
me.staticMethod(); // TypeError: me.staticMethod is not a function
```

## 프로퍼티 존재 확인

```javascript
key in object

const person = {
  name: 'Lee',
  address: 'Seoul'
};

// person 객체에 name 프로퍼티가 존재한다.
console.log('name' in person);    // true
// person 객체에 address 프로퍼티가 존재한다.
console.log('address' in person); // true
// person 객체에 age 프로퍼티가 존재하지 않는다.
console.log('age' in person);     // false

//주의

console.log('toString' in person); // true
//이는 in 연산자가 person 객체가 속한 프로토타입 체인 상에 존재하는 모든 프로토타입에서 toString 프로퍼티를 검색했기 때문이다. toString은 Object.prototype의 메소드이다.
console.log(person.hasOwnProperty('toString')); // false
//직접갖고 있는지 확인
```

## 프로퍼티 열거

```javascript
for (변수선언문 in 객체) { … }

```

**for…in 문은 객체의 프로토타입 체인 상에 존재하는 모든 프로토타입의 프로퍼티 중에서 프로퍼티 어트리뷰트 [[Enumerable]]의 값이 ture인 프로퍼티를 순회하며 열거(enumeration)한다.**



object.keys/values/entries메소드

```javascript
const person = {
  name: 'Lee',
  address: 'Seoul',
  __proto__: { age: 20 }
};

console.log(Object.keys(person)); // ["name", "address"]
```



## strict mode

쓰지말자



## Built-in Object

### 객체의 분류

객체의 3분류

표준 빌트인 객체 (전역객체의 프로퍼티)

호스트 객체 (환경에 따라 다름)

사용자 정의 객체 ()

### 표준빌트인 객체

Object,String등 내가 많이 아는것 40가지

### 원시 값과 래퍼객체

**문자열, 숫자, 불리언 값에 대해 객체처럼 접근하면 생성되는 임시 객체를 레퍼 객체(wrapper object)**라 한다.

### 전역객체

> globalThis
>
> 2020년 5월 현재, 전역 객체를 가리키는 식별자를 [globalThis](https://github.com/tc39/proposal-global)로 통일하는 제안이 stage 4에 올라와 있다. globalThis는 크롬 71, 파이어폭스 65, 사파리 12.1, Edge 79, Node.js 12.0.0 이상에 이미 구현되어 있다.