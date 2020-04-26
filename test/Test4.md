# **프론트엔드 16기** Test4

Q1) 다음 객체 리터럴을 사용하여 코드를 작성하였습니다. 메모리에 적재되는 과정을 ‘그림’을 통해 설명해 주세요. (20점)

<br>

![img](https://lh3.googleusercontent.com/pVjoac0fqNcp6VYvxSHPutOxqOdw_Qmy1DEek0lY8V3o1z6KoOYg9RiFL6Ao7z0gc1OfvwyY1ij2bdsPy2OM1id3aLdPHI96u0kbjkHWcrjKkIVR_FRIGQxNW_SgP-YyI_i3PqDa)<br>Q2) 값에 의한 전달(Pass by value)와 참조에 의한 전달(pass by reference)에 차이에 대해 설명하세요.

<br>
Q3) 다음 보기 중 객체의 프로퍼티에 대한 설명으로 옳지 않은 것은?
프로퍼티를 나열할 때는 쉼표(,)로 구분한다. 마지막 프로퍼티 뒤에는 쉼표를 사용할 수 없다. 예약어를 프로퍼티 키로 사용해도 에러가 발생하지 않는다. 이미 존재하는 프로퍼티 키를 중복 선언하면 나중에 선언한 프로퍼티가 무시된다. 식별자 네이밍 규칙을 준수하는 프로퍼티 키 이름은 따옴표를 생략할 수 있다.

<br>
Q4) 아래 코드의 실행 결과로 알맞은 것은?

<br>

![img](https://lh5.googleusercontent.com/Yho6KXHNiYobza5t70y9Mk27b8Y4rbsuZhLyCKceOIAD34UupRZIql10VNeR6HIiQHhet8KaOUoTieQ4ODle0tBZdH3plFMkpLvYgFeett31tKjy_w_-XSlLSj3r_B4fW8Ia5n_Y)

1. undefined		2. ‘foo’		3. ‘bar’	4. 1     5. ReferenceError

<br>
Q5) 아래 코드의 실행 결과와 해당 결과가 나올 수 있는 이유에 대해 설명해주세요.

<br>

![img](https://lh6.googleusercontent.com/STW0VsIpRBGCBtOlPllolT0b6Thhf9jf6MxyQUoCwybtvg5gMe9Q8kj0FYbmpnU-Fb70kNulqPLW1UxWaVZWDZON0ic5JqZ9SD4hW7jmvVxMJuqsMwsWWaCKAErevxm8PRSVsfn9)

<br>

1

문제의도: 객체리터럴이 메모리에 적재되는 과정이해

해설

![IMG_20200512_171656](https://user-images.githubusercontent.com/48181483/81659483-b9a5f600-9474-11ea-8c0c-b4f5ebe3b89c.jpg)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    var 키워드로 person 변수 식별자 선언하면 암묵적으로 undefined로 초기화한다 ⓐ

그 후 객체를 평가하여 메모리에 적재하고ⓑ

person의 참조 값을 객체가 존재하는 메모리의 선두셀을 참조하고 있는 주소를 가리키게 한다 ⓒ

<br>

2
문제 의도: 변경 가능한 객체 타입의 값과 변경 불가능한 원시 값의 구분

해설

변수에 원시 값을 갖는 변수를 할당하면 할당받는 변수에는 할당되는 변수의 원시 값이 복사되어 전달된다. 

<br>객체를 가리키는 변수를 다른 변수에 할당하면 원본의 참조 값이 복사되어 전달된다.

<br>

3

문제 의도: 프로퍼티에 대한 이해

해설: 프로퍼티는 쉼표(,)로 구분하며, 예약어를 프로퍼티 키로 사용할 수 있고 식별자 네이밍 규칙을 따르면 따옴표를 생략할 수 있다. 마지막 프로퍼티에도 쉼표를 사용할 수 있고, 중복됐을 경우 뒤가 아닌 앞이 무시된다.

<br>

4

문제 의도: 객체와 참조 방법에 대한 이해

해설

객체가 존재하고, 그 안에 프로퍼티 키와 값의 쌍들로 이루어져 있다. 이때 

string = obj[1];에는 1이라는 프로퍼티 키로써 obj에서 프로퍼티 조회를 해서 변수에 할당한다.

string = 'foo' 이 상태로 obj[string]을 하게 되면 obj['foo']를 한 것과 마찬가지이므로

콘솔 창에 1출력.

5

문제의도: 객체, 참조값의 비교 이해

해설

a와 b에는 같아 보이는(프로퍼티 키와 값이 동일한) 객체를 할당하였다. 이때 a===b를 하게 되면, 서로의 객체를 가지고 있는 메모리의 셀을 비교하게 되고 false가 출력된다 
(참조 값이 다르다). 그러나 a.name과 b.name을 참조해서 비교하게 되면 같은 문자열을 갖고 있어 true가 출력된다(값이 같다)