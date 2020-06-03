# 프론트엔드 16기 - JAVASCRIPT TEST 2

Q1) 자바스크립트에서 제공하는 원시 데이터 타입(primitive data type) 6개를 나열한 후 각 타입에 대한 설명을 **간략히** 써주세요.

Q2) 데이터 타입이 필요한 이유를 2개 이상 **간략히** 써주세요.

Q3) 일부 연산자는 다른 코드에 영향을 주는 부수 효과(side effect)가 있다. 다음 보기 중 부수 효과를 가지는 연산자는?

1.typeof

2.&&

3.++

4.=

5.!

Q4) 아래의 코드에 잘못된 점을 설명하세요.(20점)![img](https://lh6.googleusercontent.com/hhlTewl0Bl3hIDnNpETMVAdP52ORwBRCv0QGwc4o77gpm5gAct65RvanEKXfYDfO6UEcoLyrjzZAKai947HO_99sH9fcRvQD69vxpFr9pGZfMwYE0b1TESKoOqazQymMdm1pihDN)

Q5) 아래 코드의 결과를 예측하고, 결과에 대해 설명하세요(각 10점)![img](https://lh6.googleusercontent.com/-gc9qzXCr6BwcW1zwGmwH3MBebWgK2aSVHf_LoRroAP10DENbeT3WS8WmyssVH_agkGScOm3H5j5HY5KkqShkyUYz662but3x_q69Le8mVj0EVXfn5vYB_zrnF-K4MWL_CA7S_Hb)

1
출제의도 : 자바스크립트 타입에 대한 이해
<br>
해설

- 숫자(number) 타입: 숫자. 정수와 실수 구분 없이 하나의 숫자 타입만 존재
- string - 문자열, 텍스트 데이터, 16비트 유니코드
- undefined 타입: var 키워드로 선언된 변수에 암묵적으로 할당되는 값
- null 타입: 값이 없다는 것을 의도적으로 명시할 때 사용하는 값
- 불리언(boolean) 타입: 논리적 참(true)과 거짓(false)
- Symbol 타입: ES6에서 새롭게 추가된 7번째 타입

자바스크립트는 크게 두 가지의 데이터 타입이 존재하며 (원시 타입/객체 타입) 그중 원시 타입에는 6가지가 존재하고 그 이외는 모두 객체 타입이다.

데이터 타입이 필요한 이유는 2번 문제랑 연결된다.

2

출제의도: 데이터 타입이 필요한 이유

해설

- 값을 저장할 때 확보해야 하는 **메모리 공간의 크기**를 결정하기 위해
- 값을 참조할 때 한 번에 읽어 들여야 할 **메모리 공간의 크기**를 결정하기 위해
- 메모리에서 읽어 들인 **2진수를 어떻게 해석**할지를 결정하기 위해

<br>

3

출제의도: 연산자 부수효과에 대한 이해

해설 단항 연산자 중 ++,--는 1개의 피연산자를 산술연산하여 숫자 타입의 값으로 변환한다.

ex)

<br>

```javascript
>var a = '12';
<undefined
>a++
<12
>++a
<14
```

할당 연산자 =를 포함한 +=, -=등등 역시 우항에 있는 피연산자의 평가 결과를 좌항에 있는 변수에 할당한다. 변수의 값이 변하는 효과가 있다.

```javascript
>var x = 1;
<undefined
>x = x +5 ;
<6
```

4.

출제의도:개발자의 의도 파악 및 효율적이지 않는 이유 찾기

해설

Foo에 null 값을 재할당한 이유를 알 수 없다(메모리 공간이 비어있음을 _알리기 위해?)_

의도적 부재를 알리기 위함이라면, 스코프를 좁혀야 함

![IMG_20200512_161948](https://user-images.githubusercontent.com/48181483/81650897-4482f280-946d-11ea-9dc6-8897f60eb142.jpg)

메모리를 비워주려고 null을 넣어준 것 같지만 null 자체도 메모리 공간을 차지하기 때문에 의미 없는 행동이 되었다.

5

출제의도: NaN에 대한이해

해설

1.NaN

2.숫자가 아닌값을 연산했을때 나오는 결과 (NOT A NUMBER) =산술연산불가

undefined로 산술연산을 하게 되면 많은 오류들을 발생시킬 수 있다.

ex)

```javascript
var a;
var b = 1;
a + b; // a에 암묵적으로 들어간 undefined랑 숫자리터럴이 들어간 b랑 연산하여 어디에 어떻게 사용할지 추측이 불가능하다
```
