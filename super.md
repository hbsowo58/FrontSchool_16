# super

super 키워드는 함수처럼 호출할 수도 있고 this와 같이 식별자처럼 참조할 수 있는 특수한 키워드

- super를 호출하면 super class의 constructor를 호출한다
- super를 참조하면 super class의 메서드를 호출할 수 있다

---

super class 클래스의 constructor 내부에서 추가한 프로퍼티를 그대로 갖는 인스턴스를 생성

-> 서브 클래스의 constructor 생략 가능

이때 new 연산자와 함께 서브 클래스를 호출하면서 전달한 인수는 모두 서브 클래스에 암묵적으로

 정의된 디폴트 constrouctor의 super 호출을 통해 super class의 construcotor에 전달된다

<br>

super class에서 추가한 프로퍼티와 서브 클래스에서 추가한 프로퍼티를 갖는 인스턴스를 생성한다면

서브 클래스의 construcotr를 생략할 수 없다. 이때 new 연산자와 함께 서브 클래스를 호출하면서 전달한 인수 중에서 super class의 construtor에게 전달할 필요가 없는 인수는 서브 클래스의 constructor에서 호출한 super를 통해 전달한다.

<br>

### super를 호출할 때 주의할 사항

1. 서브 클래스에서 constructor를 생략하지 않는 경우, 서브 클래스의 constructor에서는 반드시 super를 호출해야 한다.
2. 서브 클래스의 constructor에서 super를 호출하기 전에는 this를 참조할 수 없다.
3. super는 반드시 서브 클래스의 constructor에서만 호출한다. 서브 클래스가 아닌 클래스 또는 함수에서 호출하면 에러를 발생시킨다.

### super 참조

1. 서브 클래스의 프로토타입 메서드 내에서 super.prop는 super class의 프로토타입 메서드 prop를 가리킨다.
2. 서브 클래스 정적 메서드 내에서 super.prop는 super class의 정적 메서드 prop를 가리킨다.

### 상속 클래스의 인스턴스 생성 과정

1. 서브 클래스의 super 호출
2. super class의 인스턴스 생성과 this 바인딩
3. super class의 인스턴스 초기화
4. 서브 클래스 construcotr로의 복귀와 this 바인딩
5. 서브 클래스의 인스턴스 초기화
6. 인스턴스 반환