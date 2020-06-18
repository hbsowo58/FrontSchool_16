# promise

비동기인 부분은 xhr.onload 뒷부분이지 앞부분이 비동기는 아니다

비동기 코드의 일부분이 비동기인것이지 전체가 비동기인것은 아니다

<br>

비동기 함수는 왜 콜백을 써야할까? return이나 전역변수에 할당하면 안되나?

-> 시점이 안맞는다. 비동기 코드가 언제 진행될지 모르기 때문이다.

<br>

자바스크립트는 비동기처리를 콜백함수 사용 -> 가독성 및 예외 처리 곤란

=> 프로미스 도입 (콜백 패턴 단점 보완)

+ 에러 처리에 유리하다(XMLHTTPRequest도 불가능한것은 x)
+ 에러는 caller 방향으로 전파된다
+ map의 콜백에서 에러 => map에게 에러전파 => map을 호출한 ex)전역

<br>

자바스크립트 '엔진'은 싱글스레드고 브라우저는 멀티 스레드이다.

비동기 함수의 에러는 유실되며, promise는 에러를 포함한 promise 객체를 만든다.

promise.all을 사용하여 해결한다(병렬) <---> race(1등만 리턴한다)

allSettled(성공/실패에 상관x)

<br>

task queue, microtask queue,  animaition queue

(일반적인 비동기 함수의콜백은 task),(promise의 콜백은 micortask) => 그리하여 더 우선시된다

<br>

fetch 호출 -> 리턴값 promise -> then,catch 사용

(http통신전용)

promise는 모든 비동기에 사용

fetch를하면 response 객체를 ressolve한 promise 객체를 반환한다

await 뒤에는 promise가 오는 자리이며 async 함수 안에서 사용한다

await는 동기처럼 작성할'때' 사용한다, 필요없다면 promiseAll을 사용하여도 된다

<br>

프로미스는 Promise 생성자 함수를 통해 인스턴스화 콜백함수를 인자로 받음(resolve와 reject함수를 인자로받음)

```javascript
const promise = new Promise((resolve, reject) =>{
    if(성공){
        resolve();
    } else{
        reject();
    }
})
```

| 상태          | 의미                                                         | 구현                                               |
| :------------ | :----------------------------------------------------------- | :------------------------------------------------- |
| pending       | 비동기 처리가 아직 수행되지 않은 상태                        | resolve 또는 reject 함수가 아직 호출되지 않은 상태 |
| **fulfilled** | 비동기 처리가 수행된 상태 (성공)                             | resolve 함수가 호출된 상태                         |
| **rejected**  | 비동기 처리가 수행된 상태 (실패)                             | reject 함수가 호출된 상태                          |
| settled       | fulfilled 또는rejected와 상관 없이 pending 이 아닌 상태, 즉 비동기 처리가 수행된 상태 | resolve 또는 reject 함수가 호출된 상태             |

<br>

Promise 객체의 상태 정보는 resolve 또는 reject 함수를 호출하는 것으로 결정된다. resolve 또는 reject 함수를 호출할 때 전달한 비동기 처리 결과 또는 에러는 Promise 객체의 후속 처리 메서드에게 전달된다.

<br>

프로미스로 구현된 비동기 함수는 Promise 객체를 반환해야 한다. 프로미스로 구현된 비동기 함수를 호출하는 측(promise consumer)에서는 Promise 객체의 후속 처리 메서드 then, catch, finally를 통해 비동기 처리 결과 또는 에러 메시지를 전달받아 후속 처리를 수행한다.

<br>

# 프로미스의 후속 처리 메서드

Promise.prototype.then

then 메서드는 두 개의 콜백 함수를 인수로 전달 받는다. 첫 번째 콜백 함수는 프로미스가 fulfilled 상태(resolve 함수가 호출된 상태)일 때 호출되고, 두 번째 콜백 함수는 프로미스가 rejected 상태(reject 함수가 호출된 상태)일 때 호출된다. then 메서드는 언제나 Promise 객체를 반환한다. then 메서드의 콜백 함수가 Promise 객체가 아닌 값을 반환하면 그 값을 resolve 또는 reject 하여 Promise 객체를 반환한다.

<br>

Promise.prototype.catch

catch 메서드는 한 개의 콜백 함수를 인수로 전달 받는다. catch 메서드의 콜백 함수는 예외(비동기 처리에서 발생한 에러와 then 메서드에서 발생한 에러)가 발생하면 호출된다. catch 메서드는then(undefined, onRejected)과 동일하게 동작한다. 따라서 then 메서드와 마찬가지로 언제나 Promise 객체를 반환한다.

<br>

- Promise.prototype.finally

finally 메서드는 한 개의 콜백 함수를 인수로 전달 받는다. finally 메서드의 콜백 함수는 프로미스의 성공(fulfilled) 또는 실패(rejected)와 상관없이 무조건 한 번 호출된다. finally 메서드는 프로미스의 상태와 상관없이 공통적으로 수행해야할 처리해야할 때 유용하다. finally 메서드도 then/catch 메서드와 마찬가지로 언제나 Promise 객체를 반환한다. finally 메서드는 2020년 5월 현재, TC39 프로세스의 stage 4에 제안되어 있다. IE를 제외한 대부분의 브라우저에서 지원하고 있다.

# 프로미스의 에러 처리

비동기 처리 결과에 대한 후속 처리는 Promise 객체가 제공하는 후속 처리 메서드 then, catch, finally를 사용하여 수행한다. 비동기 처리 시에 발생한 에러는 then 메서드의 두 번째 콜백 함수로 처리할 수 있다.

<br>

비동기 처리 시에 발생한 에러는 Promise 객체의 후속 처리 메서드 catch을 사용해서 처리할 수도 있다.

<br>

에러 처리는 catch 메서드를 사용하는 편이 보다 효율적이다. 또한 then 메서드에 두 번째 콜백 함수를 전달하는 것보다 catch 메서드를 사용하는 것이 가독성이 더 좋다.

<br>

# 프로미스 체이닝

비동기 함수의 처리 결과를 가지고 다른 비동기 함수를 호출해야 하는 경우 비동기 함수의 호출이 중첩(nesting)이 되어 복잡도가 높아지는 콜백 헬이 발생한다. Promise 객체를 반환한 비동기 함수는 프로미스 후속 처리 메서드인 then, catch, finally 메서드를 사용할 수 있다. 이 후속 처리 메서드는 모두 Promise 객체를 반환한다. 따라서 후속 처리 메서드를 체이닝(chaining)하여 호출할 수 있다. 이로써 콜백 헬을 해결한다.

<br>

# 프로미스의 정적 메서드

Promise는 주로 생성자 함수로 사용되지만 함수도 객체이므로 메서드를 가질 수 있다. Promise 객체는 5가지 정적 메서드를 제공한다.

## Promise.resolve / Promise.reject

Promise.resolve와 Promise.reject 메서드는 이미 존재하는 값을 래핑하여 Promise 객체를 생성하기 위해 사용한다.

정적 메서드 Promise.resolve 메서드는 인자로 전달된 값을 resolve하는 Promise 객체를 생성한다.

## Promise.all

Promise.all 메서드는 Promise 객체를 요소로 갖는 배열 등의 이터러블을 인자로 전달받는다. 그리고 전달받은 모든 Promise 객체를 모두 연속적으로 처리하고, 그 처리 결과를 resolve하는 새로운 프로미스를 반환한다.

## Promise.race

Promise.race 메서드는 Promise.all 메서드와 동일하게 Promise 객체를 요소로 갖는 배열 등의 이터러블을 인자로 전달받는다. Promise.race 메서드는 Promise.all 메서드처럼 모든 Promise 객체를 연속적으로 처리하는 것이 아니라 가장 먼저 처리된 Promise 객체가 resolve한 처리 결과를 resolve하는 새로운 Promise 객체를 반환한다.

## Promise.allSettled

Promise.allSettled 메서드는 Promise 객체를 요소로 갖는 배열 등의 이터러블을 인자로 전달받는다. 그리고 전달받은 모든 Promise 객체를 모두 연속적으로 처리하고 그 처리 결과를 배열로 반환한다.

# fetch

fetch 함수는 XMLHttpRequest 객체와 마찬가지로 HTTP 요청 전송 기능을 제공하는 클라이언트 사이드 Web API이다. fetch 함수는 XMLHttpRequest 객체보다 사용법이 간단하고 프로미스를 지원하기 때문에 비동기 처리를 위한 콜백 패턴의 단점에서 자유롭다. fetch 함수는 비교적 최근에 추가된 Web API로서 인터넷 익스플로어를 제외한 대부분의 브라우저에서 제공하고 있다.

fetch 함수에는 HTTP 요청을 전송할 URL과 HTTP 요청 메서드, HTTP 요청 헤더, 페이로드 등을 설정한 객체를 전달한다.

<br>

fetch 함수는 HTTP 응답을 나타내는 Response 객체를 래핑한 Promise 객체를 반환한다. fetch 함수로 GET 요청을 전송해 보자. fetch 함수에 첫 번째 인수로 HTTP 요청을 전송할 URL만을 전달하면 GET 요청을 전송한다.

<br>

fetch 함수는 HTTP 응답을 나타내는 Response 객체를 래핑한 프로미스를 반환하므로 후속 처리 메서드 then을 통해 프로미스가 resolve한 Response 객체를 전달받을 수 있다. Response 객체는 HTTP 응답을 나타내는 다양한 프로퍼티를 제공한다.

![img](https://poiemaweb.com/assets/fs-images/45-1.png)

Response 객체

Response.prototype에는 Response 객체에 포함되어 있는 HTTP 응답 몸체(body)를 위한 다양한 메서드를 제공한다. 예를 들어, fetch 함수가 반환한 프로미스가 래핑하고 있는 HTTP 응답 몸체를 취득하려면 Response.prototype.json 메서드를 사용한다. Response.prototype.json 메서드는 Response 객체에서 HTTP 응답 몸체(response.body)를 취득하여 역직렬화한다.



![image-20200615130343171](C:\Users\82109\AppData\Roaming\Typora\typora-user-images\image-20200615130343171.png)

이벤트가 발생하면 queue에 들어감, 실행은 콜스택이 비면

<br>

xhr.onload = () => {}

xhr.send로 작성한 책들도 많다

<br>

이벤트 핸들러의 return은 받을 수 없다 -> why? 브라우저가 호출하니까

<br>

프로미스: 미래에 일어날 일에 대한 보증 수표

상태가 변하면  -> ~ 콜백으로 우리가 할일 작성 -> 비동기의 표준

<br>

프로미스를 안다는 것은 비동기를 안다는 것 async/await도 promise 기반

promise -> 모든 비동기 처리할때 사용 (ECMA SCIRPT) 사양 VS XMLHTTPReqeust는 web API라서

노드환경에서 실행 x

<br>

new pormise(() => {})

<br>

then(성공콜백, 실패콜백) -> 실패콜백은 catch에서 추천

성공콜백에는 resolve한애가 옴

-> 콜백을 쓰기 싫어서 후속 처리 메서드 사용

<br>

Rest API HTTP 프로토콜

명사 + 술어(리소스)

명사 : 뭐를(메서드)

술어 : URL 뒤에 붙이다 (GET/POST/PATCH/DELETE)