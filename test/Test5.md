# 프론트엔드 16기 - JAVASCRIPT TEST 5

Q1) 다음과 그림의 1과 같이 함수 리터럴로 함수를 정의하였다 브라우저의 콘솔 창을 확인해보니 표현식이 아닌 문이 아니라는 완료 값인 undefined가 출력되었다.
그럼에도 불구하고, 변수 x를 선언하여 할당하니 에러 없이 정상적으로 동작하였다
같은 코드임에도 다르게 동작하는 이유를 설명하세요(20점)

![img](https://lh4.googleusercontent.com/-vdHCTes8ihA_ojJFJ0QA3FL6VngrCobNWFOeenNsJpL8OsPis6rCSHNT357iO2ZvePs-oi8qJJRIntQmG3hBTzcxImZ3l1lvHx6DCEIg45dBtHTKeFEcXasid8eW79txQp_9trE)

<br>

Q2) 다음 설명에 맞는 함수를 정의하고 호출하세요. 숫자를 3개 입력받아, 모두 곱하여서 반환하는 함수. 호출할 때는 2, 5, 10을 인수로 입력하세요 함수명, 매개변수명, 인수명은 모두 자유입니다.(20점)

<br>

Q3) 해당코드에 나타는 결과를 작성하고, 이유를 설명하세요 (각10점)

![img](https://lh3.googleusercontent.com/FcJWnmIR-U59Fl27vRG0_joDP51NCd7TG3NDm5n0s8LBbN0WvzvVhkokZFDLELnAusJE_uZ2cYoaCy3-xevfYBl2MTAOWoNnlKyrkBwQllfYXE7rFpc3CxyGo7uPMxeau2Pn-jqR)

<br>

Q4) 함수 선언문으로 정의한 함수는 함수 선언문 이전에 호출할 수 있다. 그러나 함수 표현식으로 정의한 함수는 함수 표현식 이전에 호출할 수 없다. 이 이유에 대해 설명해 주세요.

<br>

Q5) 다음 중 함수에 대한 설명으로 알맞지 않은 것은?

1. 함수는 함수 이름으로 호출하는 것이 아니라 함수 객체를 가리키는 식별자로 호출한다.
2. 함수 정의 방법으로는 함수 선언문, 함수 표현식, Function 생성자 함수, 화살표 함수가 있다.
3. 함수는 객체이며 호출 할 수 있으므로, 모든 객체는 호출 할 수 있다.
4. 함수는 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의한 것이다.
5. 함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자다.

<br>

1

문제 의도: 함수정의문과 함수표현식에 대한 이해

해설:

자바스크립트 엔진은 ‘문맥’에 따라 함수 선언문과 함수 표현식을 구별한다.
아래에 변수에 할당할 부분에는 ‘값’이 오는 문맥이라 함수 표현식으로 해석하였으며,
위의 경우 add는 함수 객체에 생기는 이름과 동시에 암묵적으로 식별자로 동작하지만
아래의 경우 x라는 식별자가 가리키는 메모리에 add라는 함수 객체가 있는 것이다.

<br>

2

문제 의도: 함수 정의 및 호출에 대한 이해

해설:

```javascript
function mul(a, b, c) {
  return a * b * c;
}
mul(2, 5, 10);
```

<br>

3

NaN

문제 의도: 함수호출시, 매개변수보다 인수를 적게입력하는 상황에 대한이해

해설:

함수 정의에 매개변수를 2개 입력받기로 하였으나 인수에 1개의 숫자밖에 없기 때문에 y 값을 undefined로 인식, 2+undefined는 NaN이 출력된다.

<br>

4

문제 의도: 함수 호이스팅에 대한 이해

해설:

함수 선언문으로 정의한 함수와 함수 표현식으로 정의한 함수의 생성 시점이 다르다.

함수 선언문으로 정의한 함수는 함수 호이스팅을 따른다. 때문에 런타임 이전에 자바스크립트 엔진은 함수 이름과 동일한 이름의 식별자와 함수 객체가 생성하고, 생성된 함수 객체를 식별자에 할당한다.

함수 표현식으로 정의한 함수는 변수 호이스팅을 따른다. 때문에 변수 선언은 런타임 이전에 실행되어 undefined로 초기화되지만, 변수 할당 문의 값은 런타임에 평가되므로 함수 표현식 이전에 호출할 수 없다(undefined를 호출하는 것과 같다).

<br>

5

3 함수는 객체이며 호출할 수 있으므로, 모든 객체는 호출할 수 있다.

문제 의도: 함수에 대한 이해

해설

함수는 함수 이름으로 호출하는 게 아닌, 객체를 가리키는 식별자로 호출하는 것이며 함수 이름을 선언하지 않아도 암묵적으로 자바스크립트 엔진이 할당해 준다.

함수 정의 방법에는 선언문, 표현식, Function 생성자 함수, 화살표 함수가 존재한다

함수는 일련의 과정을 문으로 구현한 것이며 코드 블록으로 감싸 실행 단위로 정의한 것이며

함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자다.

함수는 객체이나, 호출할 수 있는 함수와 호출할 수 없는 함수로 나뉜다. 순수한 객체는 호출할 수 없다
