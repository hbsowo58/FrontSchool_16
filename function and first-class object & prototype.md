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

프로토타입



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

