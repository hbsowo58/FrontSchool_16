# 프론트엔드 16기 - JAVASCRIPT TEST 8

1) 아래코드의 주석에 ?에 해당하는 결과값을 작성하고, 그 이유를 설명하시오(각10점)

![img](https://lh5.googleusercontent.com/ldzQy1eDKHCR4lsUWfjliL5eIbCTFFRM9hJVqRap6YEdZxtZYWO_CjGqbe5SSZtwcLFW_UtveD3l2344jWtIGCCrqiOsuvjRe_l5H-msi_b5kNqsNX75p7uQDuoXva59fjz-MK__)

<br>

2) 어떠한 객체의 prototype을 교체하는 방법을 작성하고, 문제점을 작성한후, 해결방법까지 작성하시오(각6점 모두맞을시 20점)

<br>

3) 아래 코드에서 obj2의 프로토타입은 무엇인가요?

![img](https://lh5.googleusercontent.com/J2vaceLMxIIbZlheP9gPlgQxeLtCF3Y2lMZ6ttikRrOCpK5yA3A4PpnfbErDXubakc-b-g6ysonCN9RyQ5KOleJPQy-WQw42kNazN8LAPmaj2NLikxn4HOB_3e01b3IaBjh57s3I)

<br>

4) 아래 코드의 실행 결과는 무엇인가요? 이러한 현상을 일컫는 용어는 무엇인가요?

<br>

5) 아래 코드의 실행결과는 무엇인가요?

<br>

1

Hi! My name is Lee
Me._name을 kim으로 자유변수를 변경시도하였지만, 자유변수가 private하여 변경불가하여 기존의 값 출력 클로저개념 필요

출제의도: 클로저, 자유변수에 대한 이해

<br>

2

```
생성자함수.prototype = {} , 인스턴스.__proto__ = {} 교체
1번의 경우 constructor가 없다
2번의 경우 prototype , constructor 둘다 없다
Object.create 사용해서 직접상속
다른방법 사용시도 정답처리 가능
```

출제의도 :객체의 prototype 교체 방법에 대한 이해

<br>

3

obj

출제의도:obj.create()메서드에 대한 이해

<br>

4

```
Hey! My name is Lee
오버라이딩 -> 프로퍼티 쉐도잉
```

출제의도: 오버라이딩 & 프로퍼티 쉐도잉에 대한 이해

<br>

5

```
false
k
k
```

출제의도: string 생성자 함수와 string함수에 대한 이해