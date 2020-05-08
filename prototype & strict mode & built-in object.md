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