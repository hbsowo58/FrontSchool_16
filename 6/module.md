# module 모듈

모듈이란? 애플리케이션을 구성하는 개별적 요소(=재사용 가능한 코드조각)

->기능을 기준으로 파일 단위로 분리

성립되는 조건은 자신만의 파일 스코프(모듈 스코프)를 가질 수 있어야함

모듈의 자산은 기본적으로 비공개 상태(캡슐화) => 개별적 존재로서 분리되어 존재

애플리케이션과 완전히 분리되면 재사용 불가능하므로 존재의미 x

=> 공개가 필요한 자산에 한정 선택적 공개 가능 (export)

공개된 모듈의 자산은 다른 모듈에서 재사용 가능 (공개된 모듈의 자산을 사용하는 모듈 = 모듈사용자)

모듈 사용자는 필요한 자산을 공개한 모듈을 스코프 내로 불러들여 재사용할 수있음(import)

<br>

ex)스코프를 나라에 비유하면, 이나라에 수출하고 저나라에서 수입해온다

<br>

# 자바스크립트와 모듈

자바스크립트는 파일스코프와 import, export 지원x

=> 파일 여러개로 분리해서 script 태그로 로드하여도 하나의 전역객체 공유 => 전역변수 중복되는 문제

node 환경은 CommonJs

# ES6 모듈

ES6 모듈 기능 추가 script 태그에 type="module" 추가 파일 확장자는 mjs 사용할 것 권장

```javascript
<script type="module" src="foo.mjs"></script>
<script type="module" src="bar.mjs"></script>

//모듈 스코프
// foo.js
var x = 'foo';

// 변수 x는 전역 변수이다.
console.log(window.x); // foo

// bar.js
// foo.js에서 선언한 전역 변수 x와 중복된 선언이다.
var x = 'bar';

// 변수 x는 전역 변수이다.
// foo.js에서 선언한 전역 변수 x의 값이 재할당되었다.
console.log(window.x); // bar
```

```html
<!DOCTYPE html>
<html>
<body>
  <script src="foo.js"></script>
  <script src="bar.js"></script>
</body>
</html>
```

HTML에서 2개의 자바스크립트 파일을 로드하면 하나의 전역 공유

<br>

<br>

```javascript
// foo.mjs
var x = 'foo';

console.log(x); // foo
// 변수 x는 전역 변수가 아니며 window 객체의 프로퍼티도 아니다.
console.log(window.x); // undefined

// bar.mjs
// 변수 x는 foo.mjs에서 선언한 변수 x와 스코프가 다른 변수이다.
var x = 'bar';

console.log(x); // bar
// 변수 x는 전역 변수가 아니며 window 객체의 프로퍼티도 아니다.
console.log(window.x); // undefined
```

```html
<!DOCTYPE html>
<html>
<body>
  <script type="module" src="foo.mjs"></script>
  <script type="module" src="bar.mjs"></script>
</body>
</html>
```

<br>

<br>

모듈 내에서 선언한 변수는 모듈 외부에서 참조할 수 없다. 모듈 스코프가 다르기 때문이다.

```javascript
// foo.mjs
const x = 'foo';

console.log(x); // foo
// bar.js
// 다른 모듈에서 선언한 변수는 모듈 외부에서 참조할 수 없다. 스코프가 다르기 때문이다.
console.log(x); // ReferenceError: x is not defined
```

<br>

<br>

만약 모듈 안에 선언한 식별자를 외부에 공개하여 다른 모듈들이 참조할 수 있게 하고 싶다면 export 키워드를 사용한다. 선언된 변수, 함수, 클래스 등 모든 식별자를 export할 수 있다. 모듈을 공개하려면 선언문 앞에 export 키워드를 사용한다. 복수의 식별자를 export할 수도 있다.

<br>

선언문 앞에 매번 export 키워드를 붙이는 것이 싫다면 export 대상을 모아 하나의 객체로 구성하여 한번에 export할 수도 있다.

<br>

다른 모듈에서 공개(export)한 식별자를 자신의 모듈 스코프 내부로 로드하려면 import 키워드를 사용한다. 다른 모듈이 export한 식별자로 import하며 ES6 모듈의 파일 확장자를 생략할 수 없다.

```javascript
// app.mjs
// 같은 폴더 내의 lib.mjs 모듈이 export한 식별자로 import한다.
// ES6 모듈의 파일 확장자를 생략할 수 없다.
import { pi, square, Person } from './lib.mjs';
//import * as lib from './lib.mjs';
//import * as LIB from './lib.mjs';


console.log(pi);         // 3.141592653589793
console.log(square(10)); // 100
console.log(new Person('Lee')); // Person { name: 'Lee' }
```

모듈이 export한 식별자를 각각 지정하지 않고 하나의 이름으로 한꺼번에 import할 수도 있다. 이때 import되는 식별자는 as 뒤에 지정한 이름의 객체에 프로퍼티로 할당된다.

모듈이 export한 식별자 이름을 변경하여 import할 수도 있다.

모듈에서 하나의 식별자 만을 export한다면 default 키워드를 사용할 수 있다.

<br>

```javascript
// foo.mjs
export default x => x * x;

// bar.mjs
import square from './foo.mjs';

console.log(square(3)); // 9
```

default 키워드를 사용하는 경우, var, let, const 키워드는 사용할 수 없다.

<br>

```javascript
// lib.mjs
export default const foo = () => {};
// => SyntaxError: Unexpected token 'const'
```

module화를 하면 좋은점 (주관적)

1. 보기에 좋다(가독성)
2. 유지보수하기 쉽다
3. 재사용하기 쉽다
4. 스코프를 통한 변수명 재사용이 가능하다

<br>

const foo = require('path') -> common js(동기)

import {} from '_' ESM

VS

AMD 비동기

---

에버그린(상록수) => 영속적이고 '지속적'인 업데이트

<br>

ES6+(개발환경) + ES.NEXT (표준사양은 아니지만 표준이 될 가능성이 농후)

Destructing, class filed

<br>

Babel + Webpack -> 프로젝트적용

SASS = 변수,함수,CSS분리 및 조합 가능