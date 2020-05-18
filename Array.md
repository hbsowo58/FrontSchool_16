# 0518 Array

왜 배열을 많이 쓰는가? 동일한 '형태'의 데이터들이 넘어오기 때문

컴포넌트란? html에 제공하지않는 태그를 만든다

 html,css선언형언어들을 가져와서 나열한다

나열되는 메서드를 잘알고 쓸 수 있어야된다(map의 활용빈도높음)

배열은 기본적으로 여러개이기 때문에 복수형으로 작성하는것이좋다

```javascript
const todos = [];
const foods = [];
```

<br>

배열(array)은 여러 개의 값을 순차적으로 나열한 자료 구조이다.

<br>

```javascript
const arr = ['a', 'b', 'c']; // 배열 리터럴 방식
```

배열이 가지고있는 값 요소(element), 자신의 위치를 갖는 인덱스(index)를 가짐 >0이상의정수

 요소에 접근할때는 대괄호 표기법 사용 arr[0] , 요소의 개수를 나타내는 length프로퍼티 보유

->순회가능

```javascript
typeof arr // object 배열은 객체이다.
```

배열 리터럴, array 생성자함수 모두 Array.prototype을 가짐

<br>

일반 객체와 배열을 구분하는 가장 명확한 차이는 “값의 순서”와 “length 프로퍼티”이다. 값의 순서(인덱스)와 length 프로퍼티를 갖는 배열은 반복문을 통해 순차적으로 값에 접근하기 적합한 자료 구조이다.

<br>

타언어에서 배열은 **밀집 배열(dense array** 이나 자바스크립트 배열은 **희소 배열(sparse array)**

**자바스크립트의 배열은 일반적인 배열의 동작을 흉내낸 특수한 객체이다.**

<br>

- 일반적인 배열은 인덱스로 배열 요소에 빠르게 접근할 수 있다. 하지만 특정 요소를 검색하거나 요소를 삽입 또는 삭제하는 경우에는 효율적이지 않다.
- 자바스크립트 배열은 해시 테이블로 구현된 객체이므로 인덱스로 배열 요소에 접근하는 경우, 일반적인 배열보다 성능적인 면에서 느릴 수 밖에 없는 구조적인 단점을 갖는다. 하지만 특정 요소를 검색하거나 요소를 삽입 또는 삭제하는 경우에는 일반적인 배열보다 빠른 성능을 기대할 수 있다.

### 배열생성

1.배열리터럴 2. Array 생성자함수 3. Array.of 4. Array.from

### 배열 요소의 참조

대괄호 표기법 사용 =  객체의 프로퍼티 키와 같은 역할

희소배열의 empty에 접근하면 undefined 출력(객체이기 때문)

### 배열 요소의 추가와 갱신

요소가 존재하지 않는 인덱스의 배열 요소에 값을 할당 새로운 요소 추가

### 배열 요소의 삭제

delete 연산자 사용가능

희소 배열을 만들지 않으면서 배열의 특정 요소를 완전히 삭제하려면 splice를 사용한다.

### 배열 메서드

**배열에는 원본 배열(배열 메소드를 호출한 배열, 즉 배열 메소드의 구현체 내부에서 this가 가리키는 객체)을 직접 변경하는 메소드(mutator method)와 원본 배열을 직접 변경하지 않고 새로운 배열을 생성하여 반환하는 메소드(accessor method)가 있다.**

앞으로 mutator는 되도록 쓰지 않는다. push같은 mutator를 쓴다면 안쓰는 방법이 없는가 고민한다

<br>

Array.isArray

Array.prototype.indexOf

Array.prototype.push

Array.prototype.pop

Array.prototype.unshift

Array.prototype.shift

Array.prototype.concat

Array.prototype.splice

Array.prototype.slice

Array.prototype.join

Array.prototype.fill

Array.prototype.includes

Array.prototype.flat

### 배열 고차함수

-> 모두 accessor

Array.prototype.sort

> sort 역시 원본배열을 고친다. 그러나 고친 자기자신을 반환한다

