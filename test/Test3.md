# 프론트엔드 16기 - JAVASCRIPT TEST 3

Q1) 숫자를 0, 양수, 음수로 나누는 if else 문이 아래와 같이 있습니다. 삼항 조건 연산자를 이용하여 if else 문을 변경하세요

<br>

![img](https://lh3.googleusercontent.com/8tdxPhzKjqP6Myn_yvfPAxu7c2sK6LtJwCEc1W-0KjWCFLlqULCdc-Fw5wBncRlTNS1uRJfssJqRN9sBCV0iZKhykpaBHM3KUD_5T3WlztEUtJSmw0fjY9Kl6W_IqOuAwZxthPb6)

<br>

Q2) 해당 코드가 메모리에 적재되는 과정을 설명하세요

<br>

![img](https://lh5.googleusercontent.com/qb57pD_N1lPOtqWzIQnrfp6c9DllmbmYEoQdoO-STrAAs-EGDox8aolby5neUgQ1WFWTszdYLgzho7gzzkNzbxCQUjY9a69dBZ3QJxlKnSod1_JTkTI_sr0C3UkGfhNQc7JITnG8)
<br>

Q3) 아래 코드의 출력되는 결과물을 작성해주세요

<br>

![img](https://lh6.googleusercontent.com/Z8tBilY7YxfY15xpFQ1AmXrkw6hSKfTb2vowySYMzn5t2nshkdk7jbBx-um0IAcZN-5k-W8IvKkwuSe81L6dYfZ8VYskwQnwBoVkyU6ctWl8qGw1OZepbBPK_Ny9PkZyTg_oy_Ei)

<br>Q4) 아래 코드를 실행했을 때 콘솔에 출력되는 결과를 적어주세요.

```javascript
for (var i = 0; i < 10; i++) {
  if (i % 2 && i % 3) console.log(i);
}
```

<br>

Q5) 자바스크립트 엔진은 불리언 타입이 아닌 값을 truthy 값 또는 falsy 값으로 구분한다. 다음 보기 중 falsy 값이 아닌 것은?

1. undefined
2. null
3. -Infinity
4. NaN
5. ''(빈문자열)

<br>

1

출제의도: if-else문을 삼항조건연산자로 변경이 가능한가?

해설

x>0? '양수' : x<0? '음수' : '0'

x>0? '양수' : (x<0? '음수' : '0') -> 추천 이것 외에도 답이 출력되면 정답

2

출제의도: number type과 string type의 메모리 적재 과정을 이해하는가?

![20200512_165245](https://user-images.githubusercontent.com/48181483/81655556-477fe200-9471-11ea-94d7-02b57ba56eae.jpg)

문자열 연산하기 위해 ⓐ와ⓑ를 메모리에 적재하고 ⓐ를 ⓒ로 문자열로 변환하여 저장한 후 연산해서 ⓓ를 반환

3

출제의도: 연산자 우선순위 & number type과 string type의 암묵적 _타입 변환을_ 이해하는가

해설

+(더하기) 보다 _(곱하기) 가 먼저 연산되므로 2 _ '10'이 먼저 연산된다. 결괏값은 '20' (곱하기는 산술연산된다)

그 후 '10' + '20' 연산되어 '1020'이 출력된다.

4
출제의도: for 문에 대한 이해

해설 i=0부터 시작하고 i<10이기 때문에 for 문안으로 들어간다, 0% 2 && 0% 3은 트루 값으로 평가되지 않기 때문에 콘솔을 출력하지 않고, i++되어 i=1이 되고, 다시 조건식에 해당 1% 2 && 1% 3는 둘 다 1이므로 조건문에 해당돼서

1출력 후 줄바꿈 2또는 3의 배수는 모두 앞 조건 또는 뒤 조건에 해당되어 0이 돼서 2,3,4,6,8,9는 해당되지 않고 10이 되면 반복문을 벗어난다 그러므로 출력되는 것은 1,5,7 모두 줄 바뀜이 발생된다.

1

5

7

5

출제의도: falsy값에 대한 이해

해설

-infinity는 falsy값이 아니다.
