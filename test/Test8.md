# 프론트엔드 16기 - JAVASCRIPT TEST 8

Q1) 생성자 함수와 인스턴스, 생성자함수.프로토타입 간의 관계를 '그림'을 통해 아시는 대로 설명하세요(20점)

![img](https://lh6.googleusercontent.com/troOeo5ht7-6vDOYNtM3qJDQDUbVoqnLuy_e3qgaqhPTW8l0o9M8jflb-sRTr1GY2WxyidIPNgY6dq1pgWCDN0Ty8s3i4M3BqcK4YZlyW__r5TTYdl6E9GyyEKmWreCSWb3MBT8A)

<br>

Q2) 다음중 옳지 않은 것은?

1. 모든 객체의 프로토타입에 접근할때는 [[Prototype]] 내부 슬롯으로 접근한다.

2. ```javascript
   __proto__ 접근자 프로퍼티를 통해 프로토타입에 접근하면 setter함수인 setter 함수가 호출된다.
   ```

3. 접근자 프로퍼티를 사용하는 이유는 상호참조를 위함이다.

4. 모든 객체는 prototype 프로퍼티를 가지며, 인스턴스의 prototype을 가리킨다.

5. Object 생성자함수는 new연산자와 호출해야한다.

<br>

Q3) 해당 코드의 주석자리에 해당하는 결과값을 작성하고, 코드의 흐름을 아는대로 설명하시오 

![img](https://lh4.googleusercontent.com/OUqaOqlYP5i9nhKnPs9HEWVqK1aLFbE8ah6_M8dteadCthEVHY1WaU-kQOMaQ0oe8TQORqHinVHT9VRD8edcOb_jVaXCNSDLIubObL0WmBqtYQQ2--nGFRvm6KEGcvk2Z49hrT1m)

<br>

Q4) 일급 객체가 되기 위한 조건 네 가지를 적어주세요.

<br>

Q5) 아래 보기 중 함수 객체에 대한 설명으로 알맞지 않은 것은?

<br>

1 

<img width="1277" alt="제목 없음" src="https://user-images.githubusercontent.com/48181483/83736544-c3460680-a68c-11ea-9977-f0a417e7ed0b.png">출제의도: 생성자함수, 프로토타입, 인스턴스간의 이해

<br>

2

모두 틀림 답없음

```
1이 아닌이유 __proto__ 로 접근한다 직접접근 x
```

```
2틀린이유 getter가 호출된다 get __proto__
```

3틀린이유 상호참조 방지를 위함

4틀린이유 함수객체만 prototype 프로퍼티를 가짐

5틀린이유 new연산자 사용하지않아도 new연산자와 호출한것처럼 동작

출제의도: 객체와 프로토타입에 대한 이해

<br>

3

1,-1

함수표현식 두개 평가하여 변수식별자에 할당, 함수객체들을 변수식별자에 객체할당함수정의문 평가후 변수할당문에 함수호출(인수로 함수를사용) 함수가 호출되어 함수를 매개변수로 사용하여 함수를 반환 그 결과값이 식별자에 할당되고 그할당결과를 출력

출제의도: 클로저에 대한 이해

4

1. 변수나 자료 구조(객체, 배열 등)에 저장할 수 있다.
2. 함수의 매개 변수에게 전달할 수 있다.
3. 무명의 리터럴로 생성할 수 있다.
4. 함수의 결과값으로 반환할 수 있다.

출제의도: 일급객체의 조건에 대한 이해

5

```
함수 객체만 __proto__ 접근자 프로퍼티를 가진다. x
함수 객체의 prototype 프로퍼티 값과 __proto__ 접근자 프로퍼티가 반환하는 값은 같다. x
```

출제의도: 함수 객체에 대한 이해

