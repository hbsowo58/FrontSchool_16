# 0519 Regular expression, regexp

### 정규 표현식이란?

정규 표현식(regular expression, regexp)은 일정한 패턴을 가진 문자열의 집합을 표현하기 위해 사용하는 형식 언어(formal language)이다.

<br>

정규 표현식은 문자열을 대상으로 **패턴 매칭 기능**을 제공한다

<br>

### 정규 표현식의 생성

정규 표현식 객체(RegExp 객체)를 생성하기 위해서는 정규 표현식 리터럴과 RegExp 생성자 함수를 사용할 수 있다. 

### RegExp 메서드

exec

test

match

### 플래그

i 대소문자 구별x 검색

g 문자열 내의 모든 패턴을 검색

m 문자열의 행이 바뀌더라도 검색

### 패턴

정규 표현식의 패턴은 검색 대상 문자열에서 검색하고 싶은 문자열의 형식을 의미한다. 검색 대상 문자열의 일부가 패턴과 일치할 때 ‘정규 표현식과 매치(match)되었다’라고 표현한다.

패턴은 `/`으로 열고 닫으며 문자열의 따옴표는 생략한다. 따옴표를 포함하면 따옴표까지도 패턴에 포함되어 검색한다. 또한 패턴은 특별한 의미를 가지는 메타문자(meta character) 또는 기호로 표현할 수 있다.

<br>

문자열 검색

```javascript
const target = 'Is this all there is?';

// 대소문자를 구별하여 'is'를 검색
const regExp = /is/;

// target이 정규 표현식과 매치하는지 테스트
regExp.test(target); // -> true
// target과 정규 표현식의 매칭 결과
target.match(regExp); // -> ["is", index: 5, input: "Is this all there is?", groups: undefined]
```

임의의 문자열

```javascript
const target = 'Is this all there is?';

// 임의의 3자리 문자열을 검색
const regExp = /.../g;

target.match(regExp);// -> ["Is ", "thi", "s a", "ll ", "the", "re ", "is?"]
```

반복 검색

```javascript
const target = 'A AA B BB Aa Bb';

// 'A'가 최소 1번, 최대 2번 반복되는 문자열을 모두 검색
const regExp = /A{1,2}/g;

target.match(regExp); // -> ["A", "AA", "A"]
```

OR 검색

```javascript
const target = 'A AA B BB Aa Bb';

// 'A' 또는 'B'를 모두 검색
const regExp = /A|B/g;

target.match(regExp);// -> ["A", "A", "A", "B", "B", "B", "A", "B"]
```

NOT 검색

```javascript
const target = 'AA BB Aa Bb 12';

// 'A' ~ 'Z' 또는 'a' ~ 'z' 또는 공백 문자가 아닌 문자가 한번 이상 반복되는 문자열을 모두 검색
const regExp = /[^A-Za-z\s]+/g;

target.match(regExp);// -> ["12"]
```

시작 위치로 검색

```javascript
const target = 'https://poiemaweb.com';

// https로 시작하는지 검사
const regExp = /^https/;

console.log(regExp.test(target));// -> true
```

마지막 위치로 검색

```javascript
const target = 'https://poiemaweb.com';

// com으로 끝나는지 검사
const regExp = /com$/;

console.log(regExp.test(target));// -> true
```

### 자주 사용하는 정규표현식

```javascript
const url = 'https://example.com';

// 'http'로 시작하는지 검사
// ^ : 문자열의 처음을 의미한다.
const regExr = /^https/;

regExr.test(url); // -> true

const fileName = 'index.html';

// 'html'로 끝나는지 검사
// $ : 문자열의 끝을 의미한다.
const regExr = /html$/;

regExr.test(fileName); // -> true

const target = '12345';

// 모두 숫자인지 검사
// [^]: 부정(not)을 의미한다. 예를 들어 [^a-z]는 알파벳 소문자로 시작하지 않는 모든 문자를 의미한다.
// [] 바깥의 ^는 문자열의 처음을 의미한다.
const regExr = /^\d+$/;

regExr.test(target); // -> true

const target = ' Hi!';

// 1개 이상의 공백으로 시작하는지 검사
// \s : 여러 가지 공백 문자 (스페이스, 탭 등) => [\t\r\n\v\f]
const regExr = /^[\s]+/;

regExr.test(target); // -> true

const id = 'abc123';

// 알파벳 대소문자 또는 숫자로 시작하고 끝나며 4 ~10자리인지 검사
// {4,10}: 4 ~ 10자리
const regExr = /^[A-Za-z0-9]{4,10}$/;

regExr.test(id); // -> true


const email = 'ungmo2@gmail.com';

const regExr = /^[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_\.]?[0-9a-zA-Z])*\.[a-zA-Z]{2,3}$/;

regExr.test(email); // -> true

const cellphone = '010-1234-5678';

const regExr = /^\d{3}-\d{3,4}-\d{4}$/;

regExr.test(cellphone); // -> true

const target = 'abc#123';

// A-Za-z0-9 이외의 문자가 있는지 검사
let regExr = /[^A-Za-z0-9]/gi;

regExr.test(target); // -> true

// 아래 방식도 동작한다. 이 방식의 장점은 특수 문자를 선택적으로 검사할 수 있다.
regexr = /[\{\}\[\]\/?.,;:|\)*~`!^\-_+<>@\#$%&\\\=\(\'\"]/gi;

regExr.test(targetStr); // -> true

// 특수 문자 제거
regExr.replace(regexr, ''); // -> abc123
```

