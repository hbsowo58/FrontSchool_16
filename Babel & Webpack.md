# Babel & Webpack

Babel = 트랜스파일링Transpiler (버전을 ES3 & ES5)등으로 변경

Webpack  = 번들링Module bundler (나눠있는 파일 합치기)



```javascript
//자신의 메뉴얼 만들기
//다운로드 받아야될 목록
Node.js
13.13.0
---
npm
6.14.4
---
Babel
@babel/cli : 7.8.4
@babel/core : 7.9.0
@babel/preset-env : 7.9.5
@babel/plugin-proposal-class-properties : 7.8.3
@babel/polyfill : 7.8.7
---
Webpack
webpack : 4.42.1
webpack-cli : 3.3.11
---
Webpack plug-in: ES6+ ⇒ ES5
babel-loader : 8.1.0
```

<br>

<br>

```javascript
npm install --save-dev @babel/core @babel/cli
//node_modules 에 babel/core ,cli 추가
//package.json 에 devDependencies에 추가 (--save-dev 명령어) 개발할때만 필요하다
//서버에는 올라가지 않는다
//package.json에 무조건 필요한 옵션은 name과 version이다

//바벨 프리셋설정 필요
npm install --save-dev @babel/preset-env //순수한 바닐라자바스크립트
npm install --save-dev @babel/preset-react // react
npm install --save-dev @babel/preset-typescript //typescript
//package.json에 3개 확인 cli,core,preset-env

//babel.config.json 만들기
{
  "presets": ["@babel/preset-env"]
}

//package.json에 scripts 추가
"scripts": {
    "build": "babel src/js -w -d dist/js"
  }
//위 npm script는 src/js 폴더(타깃 폴더)에 있는 모든 ES6+ 파일들을 트랜스파일링한 후, 그 결과물을 dist/js 폴더에 저장한다. 사용한 옵션의 의미는 아래와 같다.

//-w : 타깃 폴더에 있는 모든 파일들의 변경을 감지하여 자동으로 트랜스파일한다. (--watch 옵션의 축약형)
//-d : 트랜스파일링된 결과물이 저장될 폴더를 지정한다. (--out-dir 옵션의 축약형)

//옵션
npm install --save-dev @babel/plugin-proposal-class-properties
//클래스필드 추가
```

<br>

<br>

```javascript
//Webpack 설치
npm install --save-dev webpack webpack-cli
//packge.json 확인 webpack, webpack-cli 추가됨

//babel-loader 설치
npm install --save-dev babel-loader
//package.json 확인 및 script 변경

//webpack.config.js 생성
const path = require('path');

module.exports = {
  // entry file
  entry: './src/js/main.js',
  // 컴파일 + 번들링된 js 파일이 저장될 경로와 이름 지정
  output: {
    path: path.resolve(__dirname, 'dist/js'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        include: [
          path.resolve(__dirname, 'src/js')
        ],
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env'],
            plugins: ['@babel/plugin-proposal-class-properties']
          }
        }
      }
    ]
  },
  devtool: 'source-map',
  // https://webpack.js.org/concepts/mode/#mode-development
  mode: 'development'
};

//babel-polyfill 설치
npm install @babel/polyfill

```

entry : 진입점

@babel-polyfill은 개발 환경에서만 사용하는 것이 아니라 실제 운영 환경에서도 사용하여야 하므로 --save-dev 옵션으로 개발 설치를 하지 않도록 한다.