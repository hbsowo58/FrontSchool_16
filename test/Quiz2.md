# **JavaScript Quiz 2 (ch.Array HOF)**

Q1) 아래의 코드를 forEach 메서드를 사용하여 작성하세요.(10점)

![img](https://lh5.googleusercontent.com/BBEmn7AxXO-mu_YDfeMxN_hT57-ymYpaGS-bGzSUTWAnbKz38EGS4WIwG-m3OsSCn4yG-Kb1H_dG8EviJ4U7bHW_H0gWqFa54Lhuuz0eE1Ygd9Og01GUriegMKxHK_7zYQPstSPC)

Q2) 다음 코드의 주석에 해당하는 부분의 결과를 작성해 주세요 (10점)

![img](https://lh3.googleusercontent.com/HkuzqFr1XNK7E7_jtcr-yA6UHE28h8Rv77Ft9939KE1lY7HGsc0Rb0ZBModzNx5DXez4un_LCqETEL6BFnwivMQVnN46lmLpMNFnjY3BHPCEJAC8PPtGVz-GulRQkfjRq0yJMiwh)

<br>

Q3) 다음 코드의 주석에 해당하는 부분의 결과를 작성해 주세요(각 5점)

![img](https://lh6.googleusercontent.com/tl5s36h3eVZMUhrPOhq0sO--39uSq4aQHCQ_nWRP_ICmsAQBW2ECMGFdaKSz3oLUDwsP3OfdreJDxW4OoIiN3AcWC0HXgzSJjKpg0Q4qU85xljbVXHhRp7HtfwA-OvozOrQZRMJS)

<br>

Q4) 아래와 같은 배열에서 이름이 7글자인 사람들만 filter 메 서드를 사용해 result 변수에 할당하는 코드를 작성한 후, reulst 변수에 할당된 배열의 결과를 작성하세요(각 5점)

![img](https://lh3.googleusercontent.com/u71AFR9yaksVrh-2dL0YPXT5mEEokWxE6Wr7fRR6whp4neG9Qqv-UZz7BceDg1O7tWEnMJScQ9zCQ62N89tQ97RPN5efcuF-9alz_nytewuEVqXL-d3r1dI3o11WorS0xEEcQzcO)

<br>

Q5) 해당 코드에 주석에 해당되는 부분의 답을 작성하고, 이보다 직관적인 방법의같은 동작을 하는 코드를 작성하세요. (각 5점)

![img](https://lh6.googleusercontent.com/lsf5oZ0CQLWVR6h29AwbMEIMHJ_BNx5O8Cvn20018cjz-pHCx-Z-3DP8jHjF7RlvHE6JYq615jPEgcq4qxPH-8EcX4jFTVs-uHiBy9sCwk3dCIrKA5H3zbnLMXBH37hQXzVLm8P6)

<br>

Q6) 해당 코드의 주석에 해당하는 결과를 작성하세요

![img](https://lh4.googleusercontent.com/dF6i5BeOFbs9g8MzCuzsHb_DRcO6bopjq4rlEl5t7vvq39kA8ESJHEe1qGEspF089zdJqhFiwKH-s1aPO-a3MCAz8UhKQNVqSv_Rt6fNpyk40fbCO3GrlUKv40z7RrlKE3eG_qwJ)

<br>

Q7) 다음과 같은 배열이 존재할 때, 성별이 여성인지 구분하여 true, false 값을 갖는 배열과, number가 모두 5 이상인지 확인할 수 있는 배열을 만드는 코드를 작성하세요
Hint : some , every

![img](https://lh6.googleusercontent.com/e_fYMVDSf0oNOk5fhaL7OKYqcGuWZhE75B1UUVFY8zLr8DYeSLiwVd-ehbJamC_6G4D_uyyaNkxGBoJvEESw588SPWpiXKLaLKJSi-O9-4MEs8kEhfcpymKAzEk20o6hPvoEAfDB)

<br>

Q8) 아래의 배열을 reduce 메서드를 사용하여 누적한 값을 sum에 할당하는 코드를
작성하세요

![img](https://lh6.googleusercontent.com/N_EZdBQtod6XecqZCXAKgv4uoKLP6KLlaISg7LU9nJUtcBFWD3YQtK84CE2PoTP9ohqIIxi6UhygnJjV7hFZY6qHpwFvuFJHtB91J75Xdnrs0R2bBz1zfJq3ibwNSut_7qdsULTM)

<br>

Q9) 해당 코드의 주석에 해당하는 값을 작성하세요

![img](https://lh6.googleusercontent.com/Q4tlPHuy0TOEfnyVHQVidNWqukSTwqRpeqDzIk2vFvNmb58kiJAlkGz8usE7qO1v4ouwkVWzshkptl1eH0JgvBEKNIW3-yYYc2w03l_ejdow2vvyYgTSIvHMaM-VvyiCC8OO78O1)

<br>

Q10) 다음 코드의 결과를 작성해 주세요

![img](https://lh6.googleusercontent.com/9ypKYX835NopWD3mYD9Z4A2Br1l-u2xxHN-ckzCVb9mgyOpTGCF_wglXpK9KMGVP-853rCZGcPT2IWjU5hTxhvOLetotBRAXeR2NT_VDymdrO9qqE5aZZpqEfgJylZ56wjVcktey)

<br>

1

origins.forEach(origin => doubles.push(origin \* 2));

문제의도:For 문을 forEach 문으로 변경할 수 있는가, (forEach 내부에서 for 문이 동작하고 있다)

<br>

2

Uncaught TypeError: Cannot read property '0' of undefined at <anonymous>

문제의도: forEach 문의 결괏값은 언제나 undefined이다,

해설: pick에 담긴 결과값은 undefined이다, undefined[0]을 찾는 부분에서 타입 에러가 발생

<br>

3

true

false

문제 의도: map이 원본 배열을 건드리지 않고 새 배열을 만든다는 것을 아는가?

해설: Map 고차 함수는 원본 배열을 건드리지 않으며 새로운 배열을 만든다
위의 예제에서는 제곱 예제라서 numbers[0] , pows[0]은 둘 다 1로 true가 나오나
Numbers 와 pows가 가지고 있는 참조 값은 서로 다르다.

<br>

4

Const result = names.filter(name => name.length === 7);
[‘Jhyooun’, ‘Gahyeon’]

문제의도: Filter 메 서드에 대한 이해, filter를 작성할 수 있는가, filter 한 결과를 이해하는가

<br>

5

100
Const result = Math.max(... score);
Const result = score.length ? Math.max(... score) : 0

문제의도: reduce 코드를 해석 가능한지, Math.max의 존재를 아는지 또는 같은 역할을 하는 자신의 다른 코드 작성

<br>

6

NaN
문제 의도 :Reduce 메서드를 사용했을 때 초깃값을 전달하지 않으면 어떻게 되는지 이해

해설 : acc.price가 undefined됨 undefined + 숫자 산술연산 불가

<br>

7

students.map(student => [student.gender].some(gen => gen === 'female'));

students.map(student => [student.number].every(num => num > 5));

문제의도: some,every를 사용할 수 있는지

<br>

8

const sum = numarr.reduce((accumulator, currentValue, index, array) => accumulator + currentValue, 0);

문제 의도:reduce 코드 작성 가능한지

<br>

9

False
Filter의 결괏값과 find의 결괏값을 아느냐
Filter의 결괏값은 배열이고 find의 결괏값은 해당 요소 값이다

<br>

1, NaN, NaN

문제의도:

- map이 세 개의 인수를 부르면서 호출한다는 것을 알고 있느냐?

- parseInt에 대해 알고 있느냐?

- 추가된 인수가 무시된다는 것을 이해하고 있느냐?

  <br>

parseInt는 문자열을 숫자로 변경하면서 인수를 parseInt(“ffff”,16) 반환 65535

다만 map은 인수를 세 개로 다음과 같이 세 번 호출한다

<br>

parseInt("1", 0, [‘1’,’2’,’3’])

parseInt("2", 1, [‘1’,’2’,’3’])

parseInt("3", 2, [‘1’,’2’,’3’])

<br>

JavaScript 함수는 일반적으로 추가 인수를 무시한다

첫 번째 호출에서 두 번째 인수는 0

기본적으로 기수가 10으로 설정되어 있음을 알고 있으므로 parseInt("1",0) 반환

1기수가 0이 아니고 2보다 작 으면 NaN 문자열을 보지 않아도 함수가 반환세 번째 호출은 2기수 인수로 전달됩니다.

이것은 변환할 문자열이 숫자 "0"으로 만 구성된 이진수임을 의미합니다 "1".

parseInt 사양 (단계 11)에만 요청 기수의 유효 숫자가 아닌 첫 번째 문자의 왼쪽에 있는 문자열을 구문 분석을 시도했다. 문자열의 첫 문자는 "3"유효한 기본 2 자리가 아니므로 NaN
