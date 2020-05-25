# 0525 DOM

**DOM(Document Object Model)은 HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 트리 자료 구조이다.**

<br>

## 노드

### HTML 요소와 노드 객체

HTML 요소(HTML element)는 HTML 문서를 구성하는 개별적인 요소를 의미한다. HTML 요소는 렌더링 엔진에 의해 파싱되어 DOM을 구성하는 요소 노드 객체로 변환된다. 이때 HTML 요소의 어트리뷰트는 어트리뷰트 노드로, HTML 요소의 텍스트 콘텐츠는 텍스트 노드로 변환된다.

### 노드 객체의 타입

문서노드, 요소 노드, 어트리뷰트 노드,텍스트 노드

### 노드 객체의 상속구조

이와 같이 **DOM은 HTML 문서의 계층적 구조와 정보를 표현하는 것은 물론 노드 객체의 종류에 따라 상속을 통해 자신에 필요한 기능, 즉 프로퍼티와 메서드의 집합인 DOM API(Application Programming Interface)를 제공한다. DOM API를 통해 HTML의 구조나 내용 또는 스타일 등을 동적으로 조작할 수 있다.**

## 요소 노드 취득

id, 태그 이름, class, css 선택자

### 요소 노드 취득 가능 여부 확인

HTMLCollection과 NodeList

## 노드 탐색

### 공백 텍스트 노드

### 자식 노드 탐색

### 자식 노드 존재 확인

Node.prototype.hasChildNodes

### 텍스트 노드 탐색

요소 노드의 텍스트 노드는 요소 노드의 자식 노드이다. 따라서 요소 노드의 텍스트 노드는 firstChild 프로퍼티로 접근할 수 있다.

```javascript
document.getElementById('foo').firstChild
document.getElementById('foo').textcontent
document.getElementById('foo').textcontent = '<h1>bar</h1>'//text 갈아끼기 태그를 택스트취급
document.getElementById('foo').innerHTML = '<h1>bar</h1>' // 이런 태그를 삽입할때 사용
//innerHTML 파싱해서 자식으로 '삽입' 단, XSS에 취약 HTML5는 innerHTML의 스크립트 태그 실행x
  <script>
    // 에러 이벤트를 강제 발생시켜 자바스크립트 코드가 실행되도록 한다.
    document.getElementById('foo').innerHTML
      = `<img src="x" onerror="alert('XSS')">`;
  </script>

```

>HTML 새니티제이션(HTML sanitization)
>
>HTML 새니티제이션은 사용자로부터 입력 받은 데이터(untrusted input data)에 의해 발생할 수 있는 크로스 사이트 스크립팅 공격을 예방하기 위해 잠재적 위험을 제거하는 기능을 말한다. 새니티제이션 함수를 직접 구현할 수도 있겠지만 [DOMPurify](https://github.com/cure53/DOMPurify) 라이브러리를 사용하는 것을 추천한다.
>DOMPurify는 아래와 같이 잠재적 위험을 내포한 HTML 마크업을 새니티제이션(살균)하여 잠재적 위험을 제거한다.
>`DOMPurify.sanitize(''); // => `
>DOMPurify는 2014년 2월부터 제공되기 시작했으므로 어느 정도 안정성이 보장된 새니티제이션 라이브러리라고 할 수 있다.

### 부모 노드 탬색

Node.prototype.parentNode 프로퍼티

### 형제 노드 탐색

## 노드 정보 취득

## 요소 노드의 텍스트 조작

### nodeValue

### textContent

## DOM 조작

### innerHTML

- 보안이 약하다  스크립트 삽입공격

- 안바뀌어도 되는 상태들도 렌더링(성능↓)

- 마지막에 추가된다(삽입되는 요소의 위치를 지정할 수 없다)

  => 해결책 createElement,isertAdjacentHTML

### insertAdjacentHTML

### 노드 삽입

마지막 노드는 appendChild

지정한 위치는 Node.prototype.insertBefore(newNode, childNode) 메서드

### 노드 복사

`Node.prototype.cloneNode([deep: true | false])` 메서드는 노드 자신의 사본을 생성하여 반환한다. 

### 노드 교체

Node.prototype.replaceChild(newChild, oldChild)

### 노드 삭제

Node.prototype.removeChild(child)

### 어트리뷰트

HTML 문서의 구성 요소인 HTML 요소는 여러 개의 어트리뷰트(attribute, 속성)를 가질 수 있다. HTML 요소의 동작을 제어하기 위한 추가적인 정보를 제공하는 HTML 어트리뷰트는 HTML 요소의 시작 태그(start/openning tag)에 어트리뷰트 이름=”어트리뷰트 값”의 형식으로 정의한다.

```html
<input id="user" type="text" value="HEOBEOMSUNG">
value는 초기값 어트리뷰트의 값은 변경하지 않는다.
```

### HTML 어트리뷰트와 DOM 프로퍼티의 대응 관계

대부분의 HTML 어트리뷰트 값은 HTML 어트리뷰트 이름과 동일한 DOM 프로퍼티 키로 참조할 수 있다. 단, 아래와 같이 HTML 어트리뷰트와 DOM 프로퍼티가 언제나 1:1로 대응하는 것은 아니며 HTML 어트리뷰트 이름과 DOM 프로퍼티 키가 반드시 일치하는 것도 아니다.

- id 어트리뷰트와 id 프로퍼티는 1:1 대응하며 동일한 값으로 연동한다.
- input 요소의 value 어트리뷰트는 value 프로퍼티와 1:1 대응한다. 하지만 value 어트리뷰트는 초기 상태를, value 프로퍼티는 최신 상태를 갖는다.
- class 어트리뷰트는 className, classList 프로퍼티와 대응한다.
- for 어트리뷰트는 htmlFor 프로퍼티와 대응한다.
- td 요소의 colspan 어트리뷰트는 대응하는 프로퍼티가 존재하지 않는다.
- textContent 프로퍼티는 대응하는 어트리뷰트가 존재하지 않는다.
- 어트리뷰트 이름은 대소문자를 구별하지 않지만 대응하는 프로퍼티 키는 카멜 케이스를 따른다. (maxlength -> maxLength)

### 요소에 적용되어 있는 CSS 스타일 참조

getComputedStyle 메서드를 사용한다. 