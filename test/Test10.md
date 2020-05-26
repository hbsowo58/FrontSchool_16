# 프론트엔드 16기 - JAVASCRIPT TEST 10

Q1) 다음코드의 주석에 this가 가리키는 것을 작성하세요. (각 5점)

![img](https://lh5.googleusercontent.com/zEiXTOjKdCf1v7pWa_eLje6okD-P-REK-NEYqeDOE6E7wsSYaNBgCKI_W3DJmtRtnZ2ErHPo599QAt8Sv4qn9nqKgRO7p8ETIf_BKeZkKT4ZqO_ZzneT-tLXiwaxsNiTEhf-kPuR)

<br>

Q2) 다음중 옳은 것을 모두 고르시오.

1. this가 가리키는 값은 함수 호출에 의해 정적으로 결정된다.
2. 엄격모드는 this바인딩에 영향을 준다.
3. 자기참조변수는 코드 어디에서든 참조가능하다.
4. 렉시컬 스코프와 this바인딩은 결정 시기가 다르다
5. 일반 함수로 호출된 모든 함수내부의 this에는 전역 객체가 바인딩된다

<br>

Q3) 아래와 같이 변수가 4개 있습니다. 변수명뒤에 마침표 표기법으로 접근하니 암묵적으로 객체처럼 사용할 수 있었습니다. 이러한 현상이 발생한 이유를 적고 다음 주석에 예상되는 결과값을 작성하세요. (각 10점)

![img](https://lh3.googleusercontent.com/prBtzYh_s1bZk_HKFnTarbX7CjsagMzdg3ZHtIsefr_s48KIbbXdZ7Q1NAWwIvg-bRlXAFrhN_ecPJhDQmIotI2R3i1tTk_PGvI2skbBQuwT6gtZop7-36bGTwpHp63ZFa6ytGkW)

<br>

Q4) 아래 테이블의 빈칸을 채워주세요.

| **함수 호출 방식**                     | **this 바인딩** |
| -------------------------------------- | --------------- |
| 일반 함수 호출                         |                 |
| 메소드 호출                            |                 |
| 생성자 함수 호출                       |                 |
| Function.prototype.apply / call / bind |                 |

<br>

Q5) 아래 코드의 실행결과를 적어주세요.

![img](https://lh6.googleusercontent.com/-uEhhrPw5Gsv4MUrZ42gXpcvvFwvuSvfgyxlIrWCRSSz6RI8n8ZR4Wss6Ma5C2ScsEmqFL16MmN3gJFulLrYdRmoOzmay90jdHecovyeso7Kg2a4-q7W9yY-SGd4QUfVlz6Jw1Ap)

<br>

1

1. Squared { num: 2, getNum: ƒ } = 미래에 생성할 인스턴스
2. Window
3. { foo: "bar" } = 첫번째 인수로 전달한 test 객체
4. { name: "tiger", speed: 10, run: ƒ } = 메서드를 호출한 객체

출제의도: 함수 호출방식에 따른 객체 이해

<br>

2

this가 가리키는 값은 호출에 의해 동적으로 결정된다

출제의도:this 바인딩에 대한이해

<br>

3

둘다 Error / undefined와 null은 마침표 표기법으로 객체타입으로 변경시킬 수 없다변경되는 이유는 ‘래퍼객체’ 키워드가 들어가있으면 정답

출제의도: undefined와 null을 객체타입으로 변경가능한지 이해

<br>

4

| **함수 호출 방식**                     | **this 바인딩**                        |
| -------------------------------------- | -------------------------------------- |
| 일반 함수 호출                         | 전역 객체                              |
| 메소드 호출                            | 메소드를 호출한 객체                   |
| 생성자 함수 호출                       | 생성자 함수가 (미래에) 생성할 인스턴스 |
| Function.prototype.apply / call / bind | 첫번째 인수로 전달한 객체              |

출제의도:this 바인딩이해

<br>

5

Hi! My name is Kim

Hi! My name is Park

출제의도: 메서드 호출에 의한 this바인딩 이해