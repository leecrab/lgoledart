# 리액트 공부 시작

### 인프런
- https://www.inflearn.com/course/react-%EC%83%9D%ED%99%9C%EC%BD%94%EB%94%A9/lecture/20303?tab=curriculum

- 카카오계정 로그인


## 개발환경 세팅 방법
https://ko.reactjs.org/ 의 '시작하기' 참고

온라인 플레이그라운드 / 웹사이트에 React 추가하기 / 새 React앱 만들기(툴체인) 3가지


### 새 React 앱 만들기

    npm - 노드js기술을 이용해서 만든 앱들을 손쉽게 설치할 수 있도록 만든 도구
    노드js계의 appstore같은 느낌


### npm설치

설치하려면 node.js가 필요
https://nodejs.org/ko/ 에서 설치  (14.18.0 LTS버전 설치했음)

cmd창에서 '''npm -v'''를 입력시 버전이 뜬다면 성공적인 설치완료

npm에 대한 추가적인 강의는 https://opentutorials.org/module/4044


### create-react-app 설치
공식적으로는 npx 를 이용하는데 npm으로 설치

```
npm install -g create-react-app  
```
만약 권한이 없다고 하면 sudo를 앞에 붙여준다

```
create-react-app -V
```
로 버전확인하면 설치완료

#### npm npx 차이
- npm이 프로그램을 설치하는 거라고 생각하면,
- npx는 한번 다운로드하고 실행하고 지운다.(실행할때마다 최신상태의 버전이용가능)

#### 디렉토리 설정
바탕화면에 폴더 생성 후 create-react-app 에게 그곳을 디렉토리로 설정하기

react-app 이라는 폴더 생성

cmd창에서 
``` cmd 
cd C:\Users\SeongUng Lee\Desktop\react-app
create-react-app .
```

#### 에디터 다운로드
VSCODE 사용시 ctrl+j로 터미널창 사용가능(맥은 cmd + j) 또는 보기-모양-패널표시

```
npm run start
```
시 새로운 브라우저창이 열리며 서버가 시작됨
만약 에러가 뜨면, cd C:\Users\SeongUng Lee\Desktop\react-app 를 통해 위치 이동 후 다시 시작
서버 종료는 ctrl + c

#### JS 코딩

react-app폴더에는 public이라는 폴더가 있는데 이 안에 index.html이 있음
index.html에 &lt;body&gt;안에 &lt;div id="root"&gt; 부분이 중요...
id값이 root를 어디를 고칠 수 있는가?

src폴더 내의 index.js에서 root부분에 App을 렌더하고 있고,
```JS
ReactDOM.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>,
document.getElementById('root')
);
```
App.js에서 
```JS
//함수형
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
        Hello React!!
    </div>
  );
}

export default App;


//클래스형
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render(){
    return (
    <div className="App">
      Hello React!!
    </div>
    );
  }
}

export default App;
```

#### CSS 코딩

import index.css라는 부분이 있음.. 그부분 수정 or App.css 수정

#### 배포방법

```
npm run build
```
build라는 폴더가 생김. 그 안에 index.html은 공백과 같이 불필요한 정보를 압축함
src에서 작업한 파일을 없에고 index.html파일이 로드할 수 있게 처리해둠.

실제 서비스할때는 build안에 있는 파일을 사용함.,
web서버의 다큐먼트 루트를 build디렉토리 안쪽을 위치시킨다.

npm을 통해 설치하는 간단한 웹서버 serve가 있고
serve라는 명령어로 실행가능
그리고 build 디렉토리를 다큐먼트루트로 하겠다는 명령어가 -s
```
npm install -g serve 
serve -s build
```

## 컴포넌트 제작
App.js에서 컴포넌트 제작
```JS
class Subject extends Component {
  render(){
    return (
      <header>
        <h1>WEB</h1>
        world wide web!
      </header>
    );
  }
}

class App extends Component {
  render(){
    return (
      <div className="App">
        <Subject></Subject>
      </div>
    );
  }
}
```
**하나의 최상위 태그만 사용해야함**

여기서 App클래스나 Subject클래스는 JS문법은 아니다. JSX문법임

