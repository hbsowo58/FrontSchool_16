# **프론트엔드 16기** Test6

Q1) 두과목의 점수 평균을 내려하고 있습니다. 여기서 85가 가지는 문제점은 무엇이며,이를 해결하기위해 사용한 sum의 메모리 적재과정을 그림을 통해 작성하세요(각10점)

![img](https://lh6.googleusercontent.com/E14uIdbcwnvsRLUMJoIks-bd6uUNx2iq-D5lDuH6N7tFit9f3IiDtct24P_YbW-2TNUIUApR8MQqkqP_6oJO7ba-44A8QffMZ_i1DGB0O-64quNADXGL3DA2U8ZrAtRv6aa6YrST)

<br>

Q2) foo라는 변수를 사용한 개발자가 메모리 공간을 비우기위해 null을 할당하여 비우려고 의도하였습니다. 개발자의 의도와 다르게 동작하는 이유를 설명하고, Baz에 나오는 결과값은 무엇이며 그 이유는 무엇인가요? (각 10점,5점,5점)

![img](https://lh3.googleusercontent.com/R1AMPQr3aQ5sIxeRjT6uAF6K2VIRkUy6XzYOh_6MB19tINXVWBdioWCwP4QKlHx7jq-0z61yrdB5A_G40wyQFtcwxcNBGQglmeF9qBZyyeEF-azQAFCJGFvnxyGWTEj0R5KEsXC3)

<br>

Q3)해당코드의 결과물을 작성하세요 (20점)

![img](https://lh6.googleusercontent.com/ys9w8hsa68w-ivmV_dErFqqtFJB6S0jts6lTQakXsfoS7CMC8JUnlHJiGMjxGfimLd-DEH652o1gP_20AjeLlKbzKWQDWZeSbQcOTOuLDvrwiWQKFNOGuFumaHtFwyYN6miXSZMw)

<br>

Q4) 해당코드의 결과물을 예상하세요 (20점)

![img](https://lh4.googleusercontent.com/rxjI8D_W1MoYrdP5VEac1wNG3sL5fKPRO1GAjPSKLGywtpIbMxbA4JDxs21NjjuXe0sWabYbgvuArXFS9Lkvt8pkHqHPLkYFNMSJW3V9nZpzhV_bu61WByDvttgxJOUcMkIQluiF)

<br>

Q5)다음 설명에 맞는 함수를 정의하고 호출하세요. 점수(숫자)를 3개 입력받아, 평균을 반환하는 함수. 호출할때는 인수(100, 90, 80)을 입력하세요 함수명AVG,매개변수명(자유),인수명(KOR,ENG,MATH)입니다.(20점)

<br>

1

재사용불가

80, 90의 각각 원시값 메모리할당 연산한값 85 (재사용x)  , undefined 초기화  sum 식별자 85라는 값 참조

출제의도: 원시값의 연산후 메모리 적재 과정 이해

<br>

2

메모리공간을 비우려고 했지만, null값이 차지하므로 똑같이 메모리공간을 차지한다

NaN , bar에 undefined로 초기화되고 1+ undefined는 연산할 수 없는 값

출제의도: 원시타입 null의 명시적 부재 이해

<br>

3

11.5

연산 우선순위에 따라 2*'3' 먼저 진행 6 /4 진행 1.5 문자열 연산 '1' + 1.5 '11.5' 출력

출제의도: 연산자 우선순위와 문자열 & 숫자 연산에 대한 이해

<br>

4

undefined

obj[2]로 qes에는 'bar'라는 값이 할당되고, obj['bar']는 없는 프로퍼티 이므로 undefined 출력

출제의도: 객체 대괄호표기법에 의한 참조 이해

<br>

5

```javascript
function AVG(x,y,z){
	Return (KOR+ENG+MATH)/3
}
AVG(100,90,80);
```

출제의도: 함수 정의와 함수 호출에 대한 이해

