# 누구든지 하는 리액트:초심자를 위한 react 핵심 강좌  
이 문서는 인프런 강의를 듣고 필기 기록용으로 작성한다.  

# 목표 
_총 172분 2010-01-19_ 오픽준비 때문에 일정을 미루게 되었음.  

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


# Virual DOM
리액트는 Virtual Dom을 사용하여 데이터의 변화를 효과적으로 관리한다.
이에 대한 개념은 다음 애니메이션 영상을 통해 쉽게 이해할 수 있다.
* React and the Virtual DOM(https://www.youtube.com/watch?v=muc2ZF0QIO4)

즉, 데이터 변화가 일어나면 바로 DOM에 반영시키는것이 아닌 Virtul DOM에 한번 렌더링을 한 후, 기존 DOM과 비교하여 변화된 부분을 캐치하여 필요한 곳에만 업데이트를 해주는 것이다. 이로써, DOM변화를 최소화 시켜주는 역할을 한다.

# Webpack과 Babel
리액트 프로젝트를 하기 위해서는 위 두가지가 필요하다.

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
리액트 프로젝트는 CODESANDBOX라는 서비스를 사용하여 실습이 진행된다. https://bit.ly/beginreact  

````javascript
import React, { Component } from 'react'; //react모듈을 불러와서 사용한다.

class App extends Component { //컴포넌트를 만드는 방법 1.클래스 2.함수 여기서는 클래스 사용
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

# JSX
리액트에서 사용되는 문법으로 HTML이랑 비슷하지만, 지켜야할 규칙이 몇가지 있다.

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




# Comment
_200116_ 아직 처음 듣는 용어들이 많아서 싱숭생숭하다. 강의를 들어도 알듯말듯한 느낌이 든다. 용어를 정리하면서 대략적으로 이해는 한 것 같지만 아직 부족하다는 느낌이 든다. 언어공부를 할 때, 코드로 짜보는것도 중요하지만 이 개념이 나타나게 된 배경또한 알아야한다고 생각한다. 다음시간에는 첫강부터 한번더 복습을 해보면서 놓쳤던 부분들도 한번 더 되돌아 보는 시간을 가지도록 하자.

_200117_ jsx문법까지 기본적으로 정리를 해보았다. 저번 시간에 들은 강의를 다시 들어보니, 프로젝트 시작 전 React에 대해 기본적으로 알아야 할 개념들이 조금씩 잡히기 시작하는 것 같다. 아무래도 강의를 모두 다 듣고 복습하는 것 보다 강의 듣고 => 일시정지 후 바로 정리, 코드 실습 => 커밋 전 복습하는것이 더 효과적인 학습 방법인 것같다.