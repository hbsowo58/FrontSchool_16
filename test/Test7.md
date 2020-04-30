# **프론트엔드 16기 - JAVASCRIPT TEST 7**

Q1) 생성자 함수란 무엇이며, 객체 리터럴 방식에 비해 갖는 장점을 작성해 주세요.

<br>

Q2) 아래에 코드에 1~4에 해당하는 결과를 작성하세요.

![img](https://lh6.googleusercontent.com/jLIFT06OVQyZo-c3Cn5CdjTmaS3nZrey6fm7ajbv8htsLPbBgviHAlhLUF6-5HyOcorHMsMqbfJQMfHJDg9Aqq1Wih631hGhzuQTvGpzg_Nw2huTKDq972mRn39OomR1Wj01lJio)

<br>

Q3) this는 객체 자신의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수입니다. this가 가리키는 값은 함수 호출 방식에 따라 동적으로 결정됩니다. 아래 3가지 함수 호출 방식에 따라 결정되는 this가 가리키는 값을 알맞게 적어주세요.

| 함수 호출 방식 | this가 가리키는 값 |
| -------------- | ------------------ |
|                |                    |
|                |                    |
|                |                    |

<br>

Q4) 아래 코드는 new 연산자와 함께 생성자 함수를 호출한 예제입니다. new 연산자와 함께 생성자 함수를 호출하면 자바스크립트 엔진은 어떠한 과정을 거쳐 인스턴스를 생성하는지 설명해 주세요.

![img](https://lh5.googleusercontent.com/QNJsOdPI71xFiDWrlK-_PUyDBY-ve3WSEe6-Fz__uXVRmXDINlt5PCsle7wj4fZhEtvKp6XXkpbgi5GVgVPOrS33bN2YApAoXXJd4VNUtqllO62kh7KCYsYE1cOFGpV7HM3kq2B3)

<br>

Q5) 다음 constructor와 non-constructor에 관한 설명 중 알맞지 않은 것은?

1.  자바스크립트에서는 함수가 어디에 할당되어 있는지에 따라 메소드인지를 판단한다.
2. 함수 선언문과 함수 표현식으로 정의한 함수만이 constructor이다.
3. 함수를 일반 함수로서 호출하면 함수 객체의 내부 메소드 [[Call]]이 호출된다.
4. non-constructor인 함수 객체를 생성자 함수로서 호출하면 에러가 발생한다.
5. 메소드 축약 표현으로 정의한 함수도 new 연산자와 함께 호출하면 constructor로서 동작한다. 

<br>

1

생성자 함수란, 객체 생성 방식의 하나이며, 같은 구조를 갖는 프로퍼티를 계속 정의하지 않아도 되며 동일한 객체를 여러 개 생성할 수 있다.

문제의도: 생성자함수 정의에 대한 이해와 필요성

<br>

2

undefined, circle객체, type error , 10

문제의도:생성자함수와 일반함수호출문에 대한 이해

해설: 

1 일반함수로 호출된 변수이다. 그러므로 생성자 함수로서 호출되지 못한 빈객체 (undefined)

2 생성자함수로 호출된 결과값이 담긴 변수이다. circle객체가 담긴다

3 일반함수로 호출되어 undefined가 담긴 변수에 radius라는 프로퍼티 키를 참조하고 있다 type error

4 생성자 함수로 호출된 변수에 radius 프로퍼티 키를 참조하고있다 10출력

<br>

3

| 함수 호출 방식       | this가 가리키는 값     |
| -------------------- | ---------------------- |
| 일반 함수로서 호출   | 전역 객체              |
| 메소드로서 호출      | 메서드를 호출한 객체   |
| 생성자 함수로서 호출 | 미래에 생성할 인스턴스 |

문제의도: 호출에따른 this 바인딩을 이해하고 있는가

<br>

4

1. 암묵적으로 빈 객체를 생성(인스턴스) 후 this에 바인딩
2. 인스턴스 초기화(프로퍼티 추가, 프로퍼티 값 할당 등)
3. (생성자 함수 내부의 모든 문을 처리)
4. 암묵적으로 this(인스턴스)를 반환

문제의도:생성자 함수의 내부과정을 이해하고 있는가

<br>

5

1,5

자바스크립트에서 메서드란, 메서드 축약표현을 사용한 방법만 메서드로 정으히ㅏㄴ다

함수선언문과 함수 표현식으로 정의한 함수만이 constructor이다

함수를 일반함수로 호출하면 함수 객체의 내부 메소드 [[Call]]이 호출된다

non-constructor인 함수 객체를 생성자 함수로서 호출하면 에러가 발생한다

메서드 축약표현으로 정의한 함수도 new 연산자와 함께 호출하면 error발생