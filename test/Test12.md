# 프론트엔드 16기 - JAVASCRIPT QUIZ 12

Q1) 아래 1, 2번 라인 코드의 공통점과 차이점을 말씀해주세요.

![img](https://lh3.googleusercontent.com/sZ3Os_AGqDFbXgCQFxeNJjsULmuRYFr65WKECCTTcIoLzG1XYaZaxWUF1Qdxv4kWS8hlEvziuLhE_T4N23x4bXMuj72XO2dNclp7rpKvodhIdbgbJZ9kbGIdwcQrX8_lgewHrb_8)

<br>

Q2) 리플로우(reflow)와 리페인트(repaint)가 무엇인지 각각 설명해주세요. (장문 금지)

<br>

Q3) 다음 브라우저 환경에서의 자바스크립트 파싱과 실행에 대한 설명으로 옳지 않은 것은?

1. 자바스크립트 파싱과 실행은 렌더링 엔진이 아닌 자바스크립트 엔진이 처리한다.
2. 자바스크립트 엔진은 자바스크립트 코드를 CPU가 이해할 수 있는 저수준 언어로 변환하는 역할을 한다.
3. 파싱(parsing)은 단순한 문자열인 소스 코드를 어휘 분석하여 문법적 의미를 가지는 코드의 최소 단위인 토큰으로 분해하는 과정을 말한다.
4. AST(Abstract Syntax Tree)는 토큰에 문법적 의미와 구조를 반영한 트리 구조의 자료 구조이다.

<br>

Q4) 아래 코드에서 id 값이 banana인 요소 노드를 탐색하여 변수에 할당하는 코드를 작성해주세요.

![img](https://lh6.googleusercontent.com/j7meGuadWhc5f5J4p1DCrgSjzP8qY0jtTxSnuHHVYkU5JCWa51H2CtzfwdMysbPJyV7eCYw9we0mJtJ5b99jUmvi1vLornb2vTeVm19KIkqd3tw_GRiRoPBFArTxileNhmu9mNmA)

<br>

Q5) 요소 노드의 innerHTML 프로퍼티에 할당한 HTML 마크업 문자열은 렌더링 엔진에 의해 파싱되어 요소 노드의 자식으로 DOM에 반영된다. 이에 대한 문제점과 해결 방법을 각각 작성해주세요. (장문 금지)

<br>

1

**공통점:** HTML 파싱과 외부 자바스크립트 파일의 로드가 비동기적으로 동시에 진행된다.
**Async:** 자바스크립트의 파싱과 실행은 자바스크립트 로드가 완료된 직후 진행되며, 이때 HTML 파싱이 중단된다.
**Defer:** 자바스크립트의 파싱과 실행은 HTML 파싱이 완료된 직후(DOM 생성이 완료된 직후) 진행된다.

출제의도: async , defer의 공통점 & 차이에 대한 이해

<br>

2

**리플로우:** 레이아웃 계산을 다시 하는 것 (노드 추가/삭제, 요소의 크기/위치 변경, 윈도우 리사이징 등 레이아웃에 영향을 주는 변경이 발생한 경우에 한하여 실행)
**리페인트:** 재결합된 렌더 트리를 기반으로 다시 페인팅 하는 것

출제의도: 리플로우 & 리페인트에 대한 이해

<br>

3

파싱(parsing)은 단순한 문자열인 소스 코드를 어휘 분석하여 문법적 의미를 가지는 코드의 최소 단위인 토큰으로 분해하는 과정을 말한다.

출제의도: 토크나이징, 렉싱에 대한 이해

<br>

4

**const** banana = document.getElementById(‘banana’);
**const** banana = document.querySelector(‘#banana’);

출제의도: 요소 노드 참조에 대한 이해

<br>

5

문제점 1: 사용자로부터 입력 받은 데이터(untrusted input data)를 그대로 innerHTML 프로퍼티에 할당하는 것은 크로스 사이트 스크립팅 공격에 취약하다.
해결 방법 1: HTML sanitization(DOMPurify 라이브러리 등)
문제점 2: 기존의 노드를 제거하고 다시 파싱 과정을 수행하여 DOM을 변경한다.
해결 방법 2: 새롭게 추가할 노드만을 생성하여 DOM에 반영하면 된다. (ex. $fruits.innerHTML += `<li>...</li>`;
문제점 3: 새로운 요소를 삽입할 위치를 지정할 수 없다.
해결 방법 3: insertAdjacentHTML 메서드 사용

출제의도: innerHTML 취약점과 해결방법에 대한 이해