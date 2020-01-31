# 누구든지 하는 리액트:초심자를 위한 react 핵심 강좌  
이 문서는 인프런 강의를 듣고 필기 기록용으로 작성한다.  

# 목표 
_총 172분_  

# 프론트엔드 라이브러리
웹애플리케이션에서 여러 유저 인터페이스를 동적으로 나타내기 위해 수많은 상태를 관리해주어야 한다.  
예를 들어서 다음과 같은 코드가 있다고 가정할 때,  
````javascript
<div>
  <h1 id="username">daun</h1>
  <h2 id="score">94</h2>
  <div id="color"></div>
</div>
````

username값을 바꿔주려면 아래와 같이 해당 DOM에 접근 후 변경하는 행위를 수행해야 한다.
````javascript
var username = document.getElementById("username");
````

그러나, 프로그램의 규모가 커진다면 수많은 DOM요소들을 직접 관리하고 코드를 정리해야하므로 매우 힘든 일이다.
따라서 이에 도움을 주는 라이브러리가 등장하게 되는데 이것이 바로 Anbular, Vue, React등이다.


# Virtual DOM
리액트는 Virtual Dom을 사용하여 데이터의 변화를 효과적으로 관리한다.
이에 대한 개념은 다음 애니메이션 영상을 통해 쉽게 이해할 수 있다.
* React and the Virtual DOM(https://www.youtube.com/watch?v=muc2ZF0QIO4)

즉, 데이터 변화가 일어나면 바로 DOM에 반영시키는것이 아닌 Virtul DOM에 한번 렌더링을 한 후, 기존 DOM과 비교하여 변화된 부분을 캐치하여 필요한 곳에만 업데이트를 해주는 것이다. 이로써, DOM변화를 최소화 시켜주는 역할을 한다.

# Webpack과 Babel
리액트 프로젝트를 하기 위해서는 위 두 가지가 필요하다.

## Webpack
코드를 의존하는 순서대로 잘 합쳐서 하나 또는 여러개의 파일로 결과물을 만들어낸다.  
여러가지 파일을 하나의 파일로 만들어준다. 나중에 규칙에 따라서 분리시켜줄 수 있다  
웹프로젝트를 만들 때 전체적으로 파일들을 관리해주는 도구라고 이해하면 된다.  

![Webpack](https://github.com/jdaun/TIL/blob/master/JavaScript/img/webpack.PNG)

## Babel
자바스크립트 변환 도구
자바스크립트는 계속에서 변화하고 있지만 node.js나 웹브라우저에서 모든 문법을 지원하지 않는다.  
따라서, 이 문법을 이전 자바스크립트로 변환한다.  
우리는 JSX라는 리액트 컴포넌트를 작성하는 문법을 사용할 때 이 도구가 사용 될 것이다. 

![Babel](https://github.com/jdaun/TIL/blob/master/JavaScript/img/babel.PNG)

# 리액트 프로젝트
리액트 프로젝트는 [CODESANDBOX라는 서비스](https://bit.ly/beginreact)를 사용하여 실습이 진행된다.  

# 컴포넌트 만드는 방법
## 1. 클래스
````javascript
import React, { Component } from 'react'; //react모듈을 불러와서 사용한다.

class App extends Component {
  render() { //메소드, 반드시 js형태의 코드를 return해주어야 한다.
    return (
      <div>
        <h1>안녕하세요 리액트</h1>
      </div>
    );
  }
}
export default App;
````

## 2. 함수
_하단에 기재된 [props](https://github.com/jdaun/TIL/blob/master/JavaScript/Reactpoint.md#9-props-) 학습 후, 다시 보기_
단순히 props만 받아와서 보여주는 경우에 주로 작성한다.  
여기서는 더 이상 코드의 상단에서 컴포넌트를 불러오지 않아도 된다. 그러나! 리액트를 불러오는 코드는 계속 유지해주어야 한다.

```javascript
import React from 'react';

const MyName = ({ name }) => { //비구조화할당
  return <div>안녕하세요! 제 이름은 {name} 입니다.</div>
}

MyName.defaultProps = {
  name: 'daun'
};

export default MyName;
```

이것은 하나의 객체 형태의 파라미터, 즉 객체 내부에 있는 name값을 props로 받아와서 값을 사용하는 구조이다.  
위 문법은 비구조화할당이라고 할 수 있다. 그렇다면 '비구조화할당' 이란 간단히 무엇일까?  

### 비구조화할당   
![비구조화1](https://github.com/jdaun/TIL/blob/master/JavaScript/img/destructuring%20assignment11.PNG)  
만약 위와 같은 코드를 작성한다고 할때, 다음과 같은 방법을 사용할 수 있다.   

![비구조화2](https://github.com/jdaun/TIL/blob/master/JavaScript/img/destructuring%20assignment2.PNG)  

이를 활용하여 함수에 적용해보면,  
![비구조화3](https://github.com/jdaun/TIL/blob/master/JavaScript/img/destructuring%20assignment3.PNG)  
위와 같이 적용할 수 있다.  

즉, 전달해준 객체의 name과 age값을 하나하나 추출해서 함수에 파라미터로 넣어주게 된다.  


클래스형 컴포넌트와 함수형 컴포넌트의 주요 차이점  
state, lifecycle이라는 기능이 빠져있다. 이것은 앞으로 배우게 될 내용이므로 여기선 가볍게 넘어간다.  

그렇다면 함수형 컴포넌트는 주로 어떨때 사용할까?  
함수형 컴포넌트는 초기 마운트 속도가 아주 미세하게 좀 더 빠르고. 불필요한 기능이 없기 때문에 메모리자원 사용한다.  
주로 단순히 값을 받아와서 보여주는 용도로 사용된다.  컴포넌트를 만드는 것이 좀 더 간단하다.

# JSX
리액트에서 사용되는 문법으로 HTML이랑 비슷하지만, 지켜야 할 규칙이 몇가지 있다.

## 1. 태그는 꼭 닫혀 있어야 한다.
input이나 br태그를 작성 할 때 리액트에서는 반드시 닫아주어야 한다.
````javascript
<input type="text"></input>
<input type="text"/> //또는 셀프클로징 태그 사용
````

## 2. 두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싼다.
````javascript
<div>
  <div>
    Hello
  </div>
  <div>
    Bye
  </div>
</div>
````
그런데, 이처럼 단순히 감싸기 위해서 div를 사용하는 것은 번거로운 일이다.  
이런 상황에서는 Fragment라는 것을 사용하면 된다. (v16.3에 도입)
  
````javascript
<Fragment>
  <div>
    Hello
  </div>
  <div>
    Bye
  </div>
</Fragment>
````

## 3. JSX안에 자바스크립트 값 사용하기
JSX 내부에서 자바스크립트 값을 사용할 땐 이렇게 할 수 있다.
````javascript
import React, {Component} from 'react';

Class App extends Component{
  render(){
    const name = 'react';
    return(
      <div>
        hello {name}!
      </div>
    );
  }
}

export default App;
````

## 4. var, const, let
### var - 함수 레벨 범위(Function Level Scope)
scope가 함수 단위이다. 즉, 아래 코드에서 a값이 유효한 곳은 foo함수안 전체이다.  
더이상은 ES6에서 사용하지 않는다.
```javascript
function foo(){
  var a = 'hello';
  if (true){
    var a = 'bye';
    console.log(a); //bye
  }
  console.log(a); //bye
}
```

### let, const - 블록 레벨 스코프(Block Level Scope)
scope가 괄호 단위이다. 즉, 아래 코드에서 a값이 유효한 곳은 괄호가 열리고 닫히는 부분 까지이다.  
let은 유동적인 값이며 const는 한번 선언 후 고정적인 값이다.
```javascript
function foo(){
  let a = 'hello';
  if (true){
    let a = 'bye';
    console.log(a); //bye
  }
  console.log(a); //Hello
}
```

## 5. 조건부 렌더링  
삼항연산자나 AND연산자를 사용한다.  
리액트에서는 if문을 바로 사용할 수 없다.(JSX내에서 사용하기 위해서는 IIFE를 사용해야 한다.)  

### 삼항연산자
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    return (
      <div>
        {
          1 + 1 === 2
          ? (<div>맞다</div>)
          : (<div>틀리다</div>)
        }
      </div>
    );
  }
}

export default App;
```

### AND연산자
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    const name='jdaun!';
    return (
      <div>
        {
          name === 'jdaun' && <div>jdaun이다</div>
        }
      </div>
    );
  }
}

export default App;
```

### IIFE - 즉시 실행 함수 표현
조건이 여러개일 경우에는 보통 jsx밖에서 코드를 작성하는 것이 일반적이지만, 만약 jsx내부에서 조건부렌더링을 할 경우 IIFE를 이용해서 함수를 선언하고 바로 실행할 수 있다.
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    const value = 3;
    return (
      <div>
        {
          (function(){
            if (value === 1) return <div>1이다.</div> //if문 대신 switch문 사용 가능 
            if (value === 2) return <div>2이다.</div>
            if (value === 3) return <div>3이다.</div>
          })()
        }
      </div>
    );
  }
}

export default App;
```

또는, 화살표 함수로 바꿔서 사용할 수 있다.  
화살표 함수는 this, arguments, super의 개념이 없는 함수이다. ES6에서 자주 사용하게 될 것이다.  

```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    const value = 3;
    return (
      <div>
        {
          (() => {
            if (value === 1) return <div>1이다.</div> //if문 대신 switch문 사용 가능
            if (value === 2) return <div>2이다.</div>
            if (value === 3) return <div>3이다.</div>
          })()
        }
      </div>
    );
  }
}

export default App;
```


## 6. CSS 사용하기
리액트에서 CSS를 적용해 줄 때 HTML과는 다르게 객체형으로 넣어준다.  
이때, 속성값은 카멜 표기법을 적용한다.  
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    const style = {
      backgroundColor: 'black',
      padding: '16px',
      color: 'white',
      fontSize: '36px'
    };
    return (
      <div style={style}>
        안녕하세요!
      </div>
    );
  }
}

export default App;
```

### 실행 결과
![css](https://github.com/jdaun/TIL/blob/master/JavaScript/img/jsx_css_%EC%8B%A4%ED%96%89%EA%B2%B0%EA%B3%BC.PNG)

## 7. Class 사용하기 
리액트에서는 className으로 클래스를 적용한다.  

App.js
```javascript
import React, { Component } from 'react';
import './App.css'; //css파일 가져오기

class App extends Component { 
  render() {
    const style = {
      backgroundColor: 'black',
      padding: '16px',
      color: 'white',
      fontSize: '36px'
    };
    return (
      <div className="App">
        안녕하세요!
      </div>
    );
  }
}

export default App;
```

App.css  
```css
.App{
  background: black;
  color: aqua;
  font-size: 1rem;
  padding: 1rem;
  font-weight: 600;
}
```

### 실행결과
![class](https://github.com/jdaun/TIL/blob/master/JavaScript/img/jsx_class_%EC%8B%A4%ED%96%89%EA%B2%B0%EA%B3%BC.PNG)

## 8. 주석 작성하기
괄호로 감싸거나 JSX태그 사이에서 작성할 수 있다.
```javascript
import React, { Component } from 'react';
class App extends Component {
  render() {
    return (
      <div>
        {/*멀티라인도 예외가 아니다!*/}
        <h1
          //내가 여기에 주석을 쓸꺼야!
        >리액트</h1>
      </div>
    );
  }
}

export default App;
```


다음으로 배울 개념은 Props, State이다.
리액트에서 데이터를 다룰때 사용되는 개념

# Props와 State
## 1. Props

부모컴포넌트가 자식컴포넌트에게 값을 전달할 때 사용된다._(부모가 자식에게 넘겨주는 값)
즉, 컴포넌트 생성 시 불러와서 사용하게 되는데 위 사진에서 value가 하나의 Props가 된다. 매우 중요!  

![props](https://github.com/jdaun/TIL/blob/master/JavaScript/img/props.PNG)


MyName.js  
```javascript
import React, { Component } from 'react';
class MyName extends Component{

  static defaultProps = { //디폴트값 설정
    name: '기본이름'
  }

  render(){
    return(
      <div>안녕하세요! 제 이름은 <b>{this.props.name}</b>입니다.</div>
    );
  }
}

export default MyName;
```

App.js  
```javascript
import React, { Component } from 'react';
import MyName from './MyName'; //MyName.js 임포트 후 아래에서 렌더링해준다.

class App extends Component {
  render() {
    return <MyName name="어쩌구"/>;
  }
} 

export default App;
```
위와 같이 MyName컴포넌트를 불러와서 props값인 name에 원하는 값을 설정할 수 있다.    
이때 name에 어떠한 값도 설정되지 않는 경우에 대비하기 위해 MyName컴포넌트에서 디폴트값을 설정해 줄 수 있다.

지금까지 만든 컴포넌트는 클래스로 생성되었다.
그러나, 클래스 말고 [함수로 컴포넌트를 생성하는 방법](https://github.com/jdaun/TIL/blob/master/JavaScript/Reactpoint.md#2-%ED%95%A8%EC%88%98)이 있다.  
이것은 딱히 복잡한 기능 없이 단순히 props를 받아와서 보여주는 경우 종종 작성한다.  
아직 학습을 하지 않았다면, 다시 상단으로 올라가 확인하자.


## 2. State  
State는 컴포넌트 자기 자신이 처음부터 들고 있는 값이다.  
만약, 변화가 필요하다면 컴포넌트의 내장함수 중 하나인 setState()를 통해서 값을 변경해준다.  
값이 바뀔때마다 컴포넌트는 리랜더링 된다.  
여기서 차이점은 Props가 읽기전용이었다면, State는 값을 변경할 수 있다.  

![state](https://github.com/jdaun/TIL/blob/master/JavaScript/img/state.PNG)

Counter.js  
```javascript
import React, { Component } from 'react';

class Counter extends Component {
  state = {
    number: 0
  };

  handleIncrease = () => { //화살표로 하지 않으면 this가 무엇인지 모르게 된다.
    this.setState({
      number: this.state.number+1
    })
  }

  handleDecrease = () => {
    this.setState({
      number: this.state.number-1
    })
  }

  render() {
    return (
      <div>
        <div>카운터</div>
        <div>값: {this.state.number}</div>
        <button onClick={this.handleIncrease}>+</button>
        <button onClick={this.handleDecrease}>-</button>
      </div>
    );
  }
}

export default Counter;
```  

App.js    
```javascript
import React, { Component } from 'react';
import Counter from './Counter';

class App extends Component {
  render() {
    return <Counter />;
  }
}

export default App;
```

이때 state는 반드시 객체형으로 만들어준다.


# LifeCycle API
생명주기라고 생각하면 된다. 다음 각 3가지 중간중간 과정에서 어떤 과정을 하고 싶을 때 사용하면 된다.  

## 1. 컴포넌트가 브라우저에 나타날 때
## 2. 업데이트 될 때
## 3. 사라질 때  

다음과 같이 종류는 매우 많지만 외울 필요는 없고 상황에 따라 쓰면 된다.  

![lifecycleapi](https://github.com/jdaun/TIL/blob/master/JavaScript/img/lifecycleapi.PNG)

## Mounting  
컴포넌트가 브라우저 상에 나타나는 것

* constructor  
생성자 함수, 우리가 만든 컴포넌트가 처음 만들어 질때 실행되는 함수  
컴포넌트가 가지고 있을 state의 초기 설정 등을 한다.  
  
* getDerivedStateFromProps  
props로 받은 값을 state에 그대로 동기하고 싶을 때 사용한다.
  
* render
어떤 DOM을 만들 지, 내부 태그에는 어떤 값을 담당하면 될 지를 정한다.  

* componentDidMount  
실제 브라우저 상에 나타날 때 호출된다.  
주로 외부 라이브러리(차트)등을 사용 할때 특정 DOM에 차트를 그리는 코드를 작성할 수 있게 한다.
혹은 네트워크(ajax)요청을 할 때 사용한다.
또, 컴포넌트가 나타나고 몇초 뒤에 어떤 작업을 실행할 때 사용한다.
우리가 만든 컴포넌트가 브라우저에 나타난 작업 시점에 어떤 작업을 하겟다! 는 것을 명시해줌  
그래서 주로 특정 이벤트 리스닝(스크롤, 클릭 이벤트 등), API요청 등을 한다.

## Update
컴포넌트의 Props나 State가 바뀔 때  

* getDerivedStateFromProps  
Props의 값을 state에 동기화 하고 싶을 때 사용한다.    

* shouldComponentUpdate★
컴포넌트가 업데이트 되는 성능을 최적화하고 싶을 때 사용한다.    
true/false값 반환 가능(false->멈춤)

* getSnapshotBeforeUpdate
렌더링을 한 결과물이 브라우저 상에 반영되기 바로 직전에 호출되는 함수   
스크롤의 위치 혹은 해당 DOM의 크기 등을 사전에 가져오고 싶을 때 사용한다.    

* componentDidUpdate
작업을 마치고 컴포넌트가 업데이트 되었을 때 호출되는 함수  
state가 바꼈을 때, 이전의 상태와 지금의 상태가 다를 때 어떤 작업을 할지를 수행한다.  

## Ummounting
컴포넌트가 브라우저 상에서 사라질 때 호출되는 함수  
  
* componentWIIIUnmount
componentDidUpdate에서 설정한 리스너를 없애주는 작업을 한다.  

## 코드로 알아보기


# Comment
_200116_ 아직 처음 듣는 용어들이 많아서 싱숭생숭하다. 강의를 들어도 알듯말듯한 느낌이 든다. 용어를 정리하면서 대략적으로 이해는 한 것 같지만 아직 부족하다는 느낌이 든다. 언어공부를 할 때, 코드로 짜보는것도 중요하지만 이 개념이 나타나게 된 배경또한 알아야한다고 생각한다. 다음시간에는 첫강부터 한번더 복습을 해보면서 놓쳤던 부분들도 한번 더 되돌아 보는 시간을 가지도록 하자.

_200117_ jsx문법까지 기본적으로 정리를 해보았다. 저번 시간에 들은 강의를 다시 들어보니, 프로젝트 시작 전 React에 대해 기본적으로 알아야 할 개념들이 조금씩 잡히기 시작하는 것 같다. 아무래도 강의를 모두 다 듣고 복습하는 것 보다 강의 듣고 => 일시정지 후 바로 정리, 코드 실습 => 커밋 전 복습하는것이 더 효과적인 학습 방법인 것같다.

_200118_ props를 처음 배우게 되었다. 오늘 강의의 핵심은 props 이지만 역시나 어렵고 헷갈렸다. 자바의 상속 개념과 비슷한것 같기도 하다. 다음 시간에는 복습 후, 함수를 컴포넌트로 만드는 방법부터 학습하면 된다.

_20200126_ 드디어 props를 완료했다. 중간중간에 어려운점도 있었고 연휴로 쉬는 공백기가 있었지만 그래도 어느정도 이해한것 같아 기쁘다! 다음 시간에 배울 state도 얼른 습득해보고 싶다.
