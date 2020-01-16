# 누구든지 하는 리액트:초심자를 위한 react 핵심 강좌  
이 문서는 인프런 강의를 듣고 필기 기록용으로 작성한다.  

# 목표 
_총 172분 2010-01-19_ 오픽준비 때문에 일정을 미루게 되었음.  

## 프론트엔드 라이브러리
웹애플리케이션에서 여러 유저 인터페이스를 동적으로 나타내기 위해 수많은 상태를 관리해주어야 한다.  
예를 들어서 다음과 같은 코드가 있다고 가정할 때,  
````javascript
<div>
  <h1 id="username">daun</h1>
  <h2 id="score">94</h2>
  <div id="color"></div>
</div>
````

usrname값을 바꿔주려면 아래와 같이 해당 DOM에 접근 후 변경하는 행위를 수행해야 한다.
````javascript
var username = document.getElementById("username");
````

그러나, 프로그램의 규모가 커진다면 수많은 DOM요소들을 직접 관리하고 코드를 정리해야하므로 매우 힘든 일이다.
따라서 이에 도움을 주는 라이브러리가 등장하게 되는데 이것이 바로 Anbular, Vue, React등이다.


## Virual DOM
리액트는 Virtual Dom을 사용하여 데이터의 변화를 효과적으로 관리한다.
이에 대한 개념은 다음 애니메이션 영상을 통해 쉽게 이해할 수 있다.
* React and the Virtual DOM(https://www.youtube.com/watch?v=muc2ZF0QIO4)

즉, 데이터 변화가 일어나면 바로 DOM에 반영시키는것이 아닌 Virtul DOM에 한번 렌더링을 한 후, 기존 DOM과 비교하여 변화된 부분을 캐치하여 필요한 곳에만 업데이트를 해주는 것이다.  
이로써, DOM변화를 최소화 시켜주는 역할을 한다.

# Webpack, Babel
리액트 프로젝트를 하기 위해서는 위 두가지가 필요하다.

## Webpack
여러가지 파일을 한개로 결합하기 위해서 Webpack이라는 도구를 사용한다.
![Webpack](https://github.com/jdaun/TIL/blob/master/JavaScript/img/webpack.PNG)

## Babel
JSX를 비롯한 새로운 자바스크립트 문법들을 사용하기 위해서 Babel이라는 도구를 사용한다.
![Babel](https://github.com/jdaun/TIL/blob/master/JavaScript/img/webpack.PNG)

# Comment
_200116_ 아직 처음 듣는 용어들이 많아서 싱숭생숭하다. 강의를 들어도 알듯말듯한 느낌이 든다. 용어를 정리하면서 대략적으로 이해는 한 것 같지만 아직 부족하다는 느낌이 든다. 언어공부를 할 때, 코드로 짜보는것도 중요하지만 이 개념이 나타나게 된 배경또한 알아야한다고 생각한다. 다음시간에는 첫강부터 한번더 복습을 해보면서 놓쳤던 부분들도 한번 더 되돌아 보는 시간을 가지도록 하자.
