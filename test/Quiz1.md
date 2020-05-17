# **프론트엔드 16기** Quiz1

Q1) 아래 코드의 실행 결과를 적어주세요.

<br>

![img](https://lh5.googleusercontent.com/29x6GOnZKA3VPuGlOSTMVOS0OUoFhogKEx2K9xC4jV_Hu775NB5_1UCmPmIKvYtO39CwmO0HTrH7C5JvIfAZ0To9KiQcKF6IeRvn-SykjoujITq52eSXRg7rHxjtGubkCvPOk9P5)

<br>

Q2) 전역 변수의 문제점은 무엇인가요? (핵심만 작성, 장문 작성시 오답 처리)

<br>

Q3) 아래 코드의 실행 결과를 적어주세요.

![img](https://lh3.googleusercontent.com/94YMjK8BwyDAxRtpS59iTbGReohIrhvi5n8Y62DBIgp3PNgHBRbHZ3x1bos-QPIo2WXi76k4uXwuGJVjSITul4YNvk51vFM85QkkUTL5rfyOdNtwKpLVVbiuUiYqMzWvGTmGwZk2)

<br>

Q4) 아래 코드의 실행 결과는 무엇인가요?

![img](https://lh5.googleusercontent.com/NDYtVdhRv_dUN8XN3ksCwuYY4pxs-_p705jxTIFMupNdTiuhUE2QB1bkzQykNG4BviTua0yZcN7MdP4hDLHKkdlbrLYUO8IH95ehFHADt4Lg6lVaL4uGWTkebncmkBtT7vXDwm2l)

<br>

Q5) this는 어떻게 결정되는지 함수 호출 방식에 따라 구분하여 적어주세요.

| 호출방식                           | this |
| ---------------------------------- | ---- |
| 일반 함수                          |      |
| 생성자 함수                        |      |
| 메서드                             |      |
| Function.prototype.call/apply/bind |      |
| 화살표함수                         |      |

<br>

Q6) 아래 코드의 실행 결과를 적어주세요.

<br>

![img](https://lh5.googleusercontent.com/zuG1l4mDf-HDDP-ao3ypYInXFZhKXwtGoefTQmLf3Bua-ulfnGAjET9rJlpRYtQwgvVYClZe9Ra4A3bUieEeyeaMPfjTjxVTOwfwo-iIudr7MI3DhbH76X_zmXTE4dvT9jp4vZ9M)

<br>

Q7) 아래 코드의 실행 결과는 무엇인가요?

![img](https://lh4.googleusercontent.com/3HFZwHnTzuQFGN_bcS5AsBVp3pt4aCDTo_DRARPo2t0GxwPu7Dzwy2iaE_ClV-MAtggh5Py9Ii4vWxIX1AD8wVATOb19tFiYHDiK9O8voRzsWyzEXirfhhFTjqfWY_H3etcusCcv)

A.number B .array C. object D. NaN

<br>

Q8) 아래 코드의 실행 결과를 적어주세요.

![img](https://lh5.googleusercontent.com/blujyKcc0MAvBw2G9Un2T_YBHZ_65bMSaP9x2gM0BhRM0COFRJG90ZiTNZ48I65uF9RZFWC3c6qiTe_MZU0hsygACuUIKzvIMwi6gM4NVo0RUotg9F7BYYVBF7v9UrVSKN5JaSx8)

<br>

Q9) 일반 함수와 화살표 함수의 차이점을 적어주세요. (핵심만 작성, 장문 작성시 오답처리)

<br>

Q10) 아래 코드를 ES6 클래스 문법으로 변경하여 작성해주세요.

![img](https://lh3.googleusercontent.com/dLrSu8VgnKp9ogZ44Qlu3ZElMOtJkVuO9QLK9IK9IH7wzH4eEGoIGIWE-y4FOC_PVpT5Hj1qwG44EcdHdUu5r8Mn7s1TGRNfIeK7kw3YqbN2PW1-lWf_uehn1tMpVaIW-drypsJ1)

1

출제의도: 생성자 함수와 메서드, 변수에 대한 이해

해설

1

2

1

0

즉시 실행 함수가 실행하여 Person 예비 생성자 함수를 만들고, prototype에 increaseAge와 decreaseAge 메 서드를 할당한다.

그 후 생성자 함수를 반환하여 Person 식별자가 가리키게 한다.

person1에 인스턴스 1만들고 person2에 인스턴스 2를 만든 후 인스턴스 1메서드와 인스턴스 2메서드를 차례대로 호출 반복한다.

<br>

2

출제의도: 전역변수에대한 이해

해설

- 긴 생명 주기 (메모리 점거)
- 암묵적 결합 (모든 코드가 전역 변수를 참조하고 변경할 수 있다)
- 스코프 체인 종점에 존재 (검색 속도가 가장 느리다)
- 네임 스페이스 오염 (JS는 하나의 전역 스코프를 공유한다)

<br>

3

출제의도: for 문에 대한 이해

해설

line이라는 변수 5 , reulst라는 변수 빈 문자열 ''

가장 밖에 for 문 i = 0부터, i <5까지 1씩 증가

안에 있는 첫 번째 for 문 j1 = i랑 똑같으며, j1<4일 때까지 1씩 증가

j2=0부터 j2<i+1보다 작을 때까지 1씩 증가

<br>

가장 밖에 for 문 시작 i = 0, i<5 (통과)

두 번째 for 문 j1 =0 , j1<4 (통과)

''

j1 1증가

두번째 for문 j1 =1 , j1<4 (통과)

''''

j1 1증가

두번째 for문 j1 =2 , j1<4 (통과)

''''''

j1 1증가

두번째 for문 j1 =3 , j1<4 (통과)

''''''''

j1 1증가

두번째 for문 j1 =4 , j1<4 (통과x)

''''''''

세번째 for문 j2=0시작 j < 1 (통과)

''''''''*

j2 1증가

세번째 for문 j2=1 j < 1 (통과x)

다음줄로 넘어감

이런식으로 반복하면

```
    *
   **
  ***
 ****
*****
```

![20200519_155712](https://user-images.githubusercontent.com/48181483/82294900-d2208e00-99e9-11ea-94a1-92d08fb2ac01.jpg)

<br>

4

Hmm.. you don't have an age i guess

출제의도: 함수와 인수, 매개변수에 대한 이해

해설 {age:18}을 인수로 함수를 checkAge 함수 호출할 때, 객체라서 참조 값이 전달된다.

checkAge 함수호출문 안에서 data는 '새로운' {age:18}의 참조 값을 갖고 data에 할당한다

그러니 data = {age:18}이지만(똑같아 보이지만) data(새로운 객체의 참조 값) === {age:18}(기존의 참조 값)은, data == {age:18}은 false라 else 문이 실행된다

<br>

5

출제의도:  this바인딩에 대한이해

| 호출방식                               | this                                        |
| -------------------------------------- | ------------------------------------------- |
| 일반 함수                              | 전역객체                                    |
| 생성자 함수                            | 미래에 생성할 인스턴스                      |
| 메서드                                 | 호출한 객체                                 |
| Function.prototype.call / apply / bind | call,apply,bind에 인수로 전달한 첫번째 객체 |
| 화살표함수                             | this가 존재하지않아 상위의 this             |

6

출제의도: 생성자 함수와 메서드, this에 대한 이해

해설

200

TypeError

<br>

최초 즉시 실행 함수가 평가되면서 함수 객체를 만들고 Square라는 예비 생성자 함수(파스칼 케이스로 보아) 및 prototype에 getArea라는 메서드를 할당 후 Square 생성자 함수를 리턴해 Square라는 식별자에 할당하였습니다.

<br>

그 후 Square(10,20)이라는 일반 함수로 호출을 하였고, square라는 변수에 할당하였는데, 일반 함수로 호출하였을 때의 this는 브라우저 환경에서 window를 가리키게 돼서 window.width, height가 할당되고 Square 생성자 함수는

return 문이 없어서 undefined를 반환합니다, 현재 square는 undefined 상태

두 번째 getArea라는 식별자는 인스턴스의 메서드를 가리키게 만들었습니다

그 후 getArea를 호출하게 되면, 프로토타입 체인상에서 getArea를 호출하여 200출력

square.getArea()를 호출하게 되면 undefined.getArea이므로 typeError가 발생하게 됩니다.

<br>

7

object

출제의도: 매개변수로 전달된 ... rest 파라미터에 대한 이해

해설

```javascript
function getAge(...args){
    console.log(args); // [20]
    console.dir(args); // Array
    console.log(typeof args) // object
}
```
args를 ... 연산자를 통해 배열화, 다만 배열 타입은 존재하지 않고 객체 타입

<br>

8

cat

dog

NaN

출제의도:  논리연산자에 대한 이해

해설

&& 논리연산자는 피연산자중 한값을 반환 앞에것을 true로 할 수 있는경우 뒤에것 반환 cat

|| 논리연산자는 피연산자중 한값을 반환 앞에것을 true로 할 수 있는경우 앞에것 반환 dog

1 && 0 앞에것을 true로 할 수 있으므로 뒤값 0 = falsy값 NaN

<br>

9

- 화살표 함수는 인스턴스를 생성할 수 없는 non-constructor이다.
- 화살표 함수는 중복된 매개 변수 이름을 선언할 수 없다.
- 화살표 함수는 함수 자체의 this, arguments, super, new.target 바인딩을 갖지 않는다.

출제의도: 화살표함수에 대한 이해

<br>

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    static sayHi() {
        console.log(‘Hi!’);
    }
    
    getAge() {
        return this.age;
    }
}

```

출제의도: class에 대한 이해 및 변환

해당 코드는 즉시 실행함 수로 Person 이란 식별자에 할당한 예비 생성자 함수 Person이며, 그 안에는 정적 메서드 sayHi와 프로토타입 메서드 getAge 존재 정적 메서드는 static 키워드 사용 인스턴스 부분은 construtor에,

prototype 메 서드는 protype 키워드 붙이지 않고 작성