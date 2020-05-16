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

<br>

<br>

Q6) 아래 코드의 실행 결과를 적어주세요.

<br>

![img](https://lh5.googleusercontent.com/zuG1l4mDf-HDDP-ao3ypYInXFZhKXwtGoefTQmLf3Bua-ulfnGAjET9rJlpRYtQwgvVYClZe9Ra4A3bUieEeyeaMPfjTjxVTOwfwo-iIudr7MI3DhbH76X_zmXTE4dvT9jp4vZ9M)

<br>

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









