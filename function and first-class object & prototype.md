

# 2020/05/06 function and first-class object & prototype

```javascript
function foo(){
	console.log(this)
}
// foo는 호출하기전까지 어떤목적인지 알 수 없다 (일반함수/생성자함수)
// this도 마찬가지로 호출전까지 어떤것을 가리키는 식별자인지 알 수 없다

foo(); // 일반함수 호출의 경우 전역객체
new foo(); //new 연산자를 사용한 생성자함수의 호출의 경우 foo{} 인스턴스 객체 (인스턴스를 만든 객함수명 =foo)

fucntion Foo(name){
    this.name = name;
    this.sayHi = function (){};
    //this.sayHi() => {}; 불가 this문제
    //this.sayHi 불가 일반객체에서만 축약표현가능
}
//*생성자함수의 메서드는 '일반함수'형태로만 작성가능

const f = new Foo('LEE')
f.sayHi();

//화살표함수, 메소드축약표현은 new 연산자를 사용하면 안됨 (es6이전은 모두 호출가능)

```

<br>

일급 객체

1. 무명의 리터럴로 생성할 수 있다. 즉, 런타임에 생성이 가능하다.
2. 변수나 자료 구조(객체, 배열 등)에 저장할 수 있다.
3. 함수의 매개 변수에게 전달할 수 있다.
4. 함수의 결과값으로 반환할 수 있다.

<br>

## 프로토타입

자바스크립트는 프로토타입 기반의 객체지향언어이며, 객체란 속성을 통해 여러 개의 값을 하나의 단위로 구성한 복합적인 자료구조

<br>

객체지향 프로그래밍에서 상태를 나타내는 데이터와 상태를 조작하는 동작을 논리적으로 묶는다. 상태를 프로퍼티 동작을 메서드라고 한다

<br>

상속이란, 객체지향프로그래밍에서 어떤 객체의 프로퍼티나 메서드를 다른 객체가 사용할 수 있는 것을 의미한다. 목적은 코드의 재사용이다.

<br>

생성자 함수란 객체 생성 방식의 한 가지이며, 동일한 구조의 프로퍼티 또는 메서드를 가진 객체들을 여러 개 양산할 때 유용하다

인스턴스에서 프로퍼티는 대부분 다른 값을 가지지만 메서드는 동일한 경우가 많은데 같은 메서드를 중복 생성하는 문제점을 해결하기 위해 상속을 통해 해결하려 하였고 자바스크립트에서는 프로토타입을 기반으로 상속을 구현한다.

<br>

프로토타입(객체) = 부모 역할을 하는 객체(정의)
객체를 이용한 객체지향 프로그래밍(상속 목적)
다른 객체에 공유 프로퍼티(메서드 포함) 제공
모든 객체는 [[Prototype]] 내부 슬롯 보유, 슬롯의 값은 '참조'값
<br>
[[Prototype]]에 저장되는 타입은 객체 생성 방식에 의해 결정.

1. 객체 리터럴: Object.prototype
2. 생성자 함수: prototype 프로퍼티에 바인딩 된 객체

모든 객체는 하나의 프로토타입의 값을 갖는다([[Prototype]] = null인 객체는 없다)
모든 프로토타입은 생성자 함수와 연결된다(객체, 프로토타입, 생성자 함수는 연결)
[[prototype]] 내부 슬롯에 직접접근 x

```
__proto__접근자 프로퍼티를 통해 간접적으로 접근
```

<br>



```javascript
console.log(person.hasOwnProperty('__proto__')); // object.prototype에 존재

// __proto__ 프로퍼티는 모든 객체의 프로토타입 객체인 Object.prototype의 접근자 프로퍼티이다.
console.log(Object.getOwnPropertyDescriptor(Object.prototype, '__proto__')); //object에 존재
```



```javascript
const p = {
  name: 'heo'
};

console.log(p.hasOwnProperty('name'));
//-> 경고문이 생기는 이유? person 인스턴스가 object.prototype과 무조건 연결되어있어야한다.
```

