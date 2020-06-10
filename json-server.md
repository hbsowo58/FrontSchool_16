# json-server실습

```javascript
//json 서버 구축
npm init -y
npm i json-server
//db.sjon 생성 및 구축
//package.json에 scripts부분에 "start": "json-server --watch db.json" 변경
>npm start
//public폴더생성 index.html
// Resources로 루트로접근
+npm i -g nodemon으로 서버 껏다 켜도되지 않게 추가
```

클라이언트가 서버에게 주는 정보(payload) -> post에선 필요 get에선 필요없지?

```javascript
//get
```

동일 출처 위반정책 cors(뷰는 5500에서 받고, api는 3000에서 받는등) 다를때



```javascript
//get
const get = (url, callback) => {
  const xhr = new XMLHttpRequest();
  //1. XMLhttpRequest 생성자함수를 호출하여 xhr 인스턴스를 생성한다.
  // xhr.open('GET', 'http://localhost:3000/todos');절대경로
  xhr.open('GET', url); //상대경로
  //2. open은 인스턴스에 대한 초기화 작업을 한다 / 함수의 매개변수를 보면 힌트를 얻을 수 있다.
  // 절대 경로와 상대 경로를 선택하는 방법은 출처가 동일할때를 기준
  xhr.send()
  //3. open까지는 준비만 한거고, send부터 요청이 날아간것이다.
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) { // 서버가 성공했냐 실패했냐에 따라 status에 값을 나눠서 담아줌 200GET 201POST
      callback(JSON.parse(xhr.response));
    } else {
      console.log(xhr.status);
    }
  };
  //4. 수신은 이벤트로 한다 이벤트 핸들러 프로퍼티 방식 성공/실패가 나뉜다
};

get('/todos', _todos => {
  todos = _todos;
  render(todos);
});
```

```javascript
//post
const post = (url, payload, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('POST', url);
  xhr.setRequestHeader('content-type', 'application/json');
  xhr.send(JSON.stringify(payload))
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) {
      callback(JSON.parse(xhr.response));
    } else {
      console.log(xhr.status);
    }
  };
};

const payload = {
  id: 4,
  content: 'angular',
  completed: false
}


post('/todos', payload, todo => {
  todos = [todo, ...todos];
  render();
});

//get과 post의 차이중 xhr.setRequestHeader('content-type', 'application/json'); 포함
```

```javascript
//post, delete 추가 code
let todos = [];
const $pre = document.querySelector('pre');
const render = () => {
  $pre.textContent = JSON.stringify(todos, null, 2);
};
const get = (url, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('GET', url);
  xhr.send();
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) {
      // Success!
      callback(JSON.parse(xhr.response));
    } else {
      // Fails!
      console.error(xhr.status);
    }
  };
};
const post = (url, payload, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('POST', url);
  xhr.setRequestHeader('content-type', 'application/json');
  xhr.send(JSON.stringify(payload));
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) {
      // Success!
      callback(JSON.parse(xhr.response));
    } else {
      // Fails!
      console.error(xhr.status);
    }
  };
};
const patch = (url, payload, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('PATCH', url);
  xhr.setRequestHeader('content-type', 'application/json');
  xhr.send(JSON.stringify(payload));
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) {
      // Success!
      callback(JSON.parse(xhr.response));
    } else {
      // Fails!
      console.error(xhr.status);
    }
  };
};
const remove = (url, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('DELETE', url);
  xhr.send();
  xhr.onload = () => {
    if (xhr.status === 200 || xhr.status === 201) {
      // Success!
      callback(JSON.parse(xhr.response));
    } else {
      // Fails!
      console.error(xhr.status);
    }
  };
};
get('/todos', _todos => {
  todos = _todos;
  const payload = { id: 4, content: "React", completed: false };
  post('/todos', payload, todo => {
    todos = [todo, ...todos];
    const completed = !todos.find(todo => todo.id === 4).completed;
    patch('/todos/4', { completed }, _todo => {
      todos = todos.map(todo => todo.id === 4 ? { ...todo, ..._todo } : todo);
      remove('/todos/4', _ => {
        todos = todos.filter(todo => todo.id !== 4);
        render();
      });
    });
  });
});
```

```javascript
//module 맛보기
//ESM VS MODULE
//ESM 방식
<script type="module" src="js/app.js"></script>
//스크립트 태그에 인라인방식 + import export --아직까지 사용하지못함
//module 방식 -> webpack
```

