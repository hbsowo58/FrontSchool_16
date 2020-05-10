# 0511 this

### this 키워드

메서드가 자신이 속한 객체의 프로퍼티를 참조하려면 자신이 속한 객체를 가리키는 식별자를 참조할 수 있어야한다

<br>

**this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(Self-referencing variable)이다. this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메소드를 참조할 수 있다.**

<br>

this는 자바스크립트 엔진에 의해 암묵적으로 생성되며 코드 어디에서든지 참조할 수 있다. 함수를 호출하면 arguments 객체와 this가 암묵적으로 함수 내부에 전달된다. 함수 내부에서 arguments 객체를 지역 변수처럼 사용할 수 있는 것처럼 this도 지역 변수처럼 사용할 수 있다. 단, **this가 가리키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.**

<br>

> 바인딩
>
> 바인딩(binding)이란 식별자와 값을 연결하는 과정을 의미한다. 예를 들어 변수는 할당에 의해 값이 바인딩된다.

<br>

### 함수호출 방식과 this바인딩

> 렉시컬 스코프와 this 바인딩은 결정 시기가 다르다.
>
> 함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프(lexical scope)는 함수 정의가 평가되어 함수 객체가 생성되는 시점에 상위 스코프를 결정한다. this에 바인딩될 객체는 함수 호출 시점에 결정된다.

호출방식

1. 일반 함수 호출
2. 메소드 호출
3. 생성자 함수 호출
4. Function.prototype.apply/call/bind 메소드에 의한 간접 호출

### 메소드 호출

메소드 내부의 this에는 메소드를 호출한 객체, 즉 메소드 이름 앞의 마침표(.) 연산자 앞에 기술한 객체가 바인딩된다. 주의할 것은 메소드 내부의 this는 메소드를 소유한 객체가 아닌 메소드를 호출한 객체에 바인딩된다는 것이다.

```javascript
const person = {
  name: "Lee",
  getName() {
    // 메소드의 this는 메소드를 호출한 객체에 바인딩된다.
    return this.name;
  },
};

// 메소드 getName을 호출한 객체는 person이다.
console.log(person.getName()); // Lee
const anotherPerson = {
  name: "Kim",
};
// 메소드 getName을 anotherPerson 객체의 메소드로 할당
anotherPerson.getName = person.getName;

// 메소드 getName을 호출한 객체는 anotherPerson이다.
console.log(anotherPerson.getName()); // kim

// 메소드 getName을 변수에 할당
const getName = person.getName;

// 메소드 getName을 일반 함수로 호출
console.log(getName()); // ''
// => getName 함수 내부에서 참조한 this.name은 window.name과 같다
// window.name은 브라우저 창의 이름을 나타내는 빌트인 프로퍼티이며 기본값은 ''이다.
// 만약 Node.js 환경에서 실행하면 undefined가 출력된다.
```

![image-20200511154820886](C:\Users\82109\AppData\Roaming\Typora\typora-user-images\image-20200511154820886.png)
