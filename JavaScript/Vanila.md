# Vanila.js
노마드코더의 ['바닐라 JS로 크롬 앱 만들기'](https://academy.nomadcoders.co/p/javascript-basics-for-absolute-beginners-kr)챌린지를 수행하며 기록한 문서입니다.  
기간: 6월 1일 ~ 6월 15일  
## 목차
* [배우는 컨셉](#배우는-컨셉)
* [기능](#기능)

* [1일차](#1일차)
* [2일차](#2일차)
* [3일차](#3일차)

## 배우는 컨셉
* VanillaJS
* ES5 vs ES6
* Variables
* let, const, var
* Data Types on JS
* Arrays
* Objects
* Functions
* Modifying DOM
* Conditions
* Local Storage
* Ajax
* Geolocation

## 기능
* 할일목록 (To Do List)
* 시계 (Clock)
* 현재 지역 날씨 (Weather with Geolocation)
* Momentum App 클론코딩

## 1일차
### JavaScript
* 웹에 쓰이는 하나뿐인 프로그래밍 언어   
* 웹에 인터렉티브한 옵션을 주고 싶을 때 사용 
* 모든 브라우저는 JavaScript를 사용한다. => 매우 심플
* 실시간을 만들수 있다. ex.실시간채팅 (socket.io)
* 앱을 만들 수 있다.
* [three.js](https://threejs.org/): 자바스크립트 3D 기능 모음 사이트
* [impact.js](https://impactjs.com/): 자바스크립트로 만든 게임 사이트

### Vanila.js
* [vanila.js](http://vanilla-js.com/)
* 라이브러리나 프레임워크가 아닌 진짜 순순한 JS를 배운다. => 웹에서의 기초 언어를 배운다.
* vaila.js를 배우고 난 후 => 라이브러리, 프레임워크 등등을 배우자.
* [repl.it](https://repl.it/): 다운로드 하지 않아도 되는 에디터, 소규모 프로젝트를 보여줄 때 적합.  
* js파일은 항상 body마지막에 넣는다.

## 2일차
### 변수
모든 Expression은 한 줄에 있어야 하며 ;로 끝을 맺는다.  
단, instruction은 ;를 쓰지 않는다.  
* Create + Initialize
  * let
    ```javascript
    let a = 221;
    ```
    변수를 초기화하거나 생성할 때 let을 써야 한다. 사용할때는 쓰지 않아도 된다.
  * const
    ```javascript
    const a = 221;
    ```
    constant상수라는 뜻, 안정적, 변수의 값이 바뀌지 않길 원하는 경우 사용한다.  
    첫 사용은 const로, 진짜 필요할 때만 let!
   * var  
   3년전엔 var을 사용했지만 요즘엔 바뀌는건 let, 바뀌지 않는건 const를 사용한다.  
* 프로그래머로서 모든 에러를 읽을 줄 알아야 한다.
* 코멘트(주석 처리)
  메모를 하고 싶을 때 사용  
  * // 한줄짜리 주석
  * /* */ 두줄짜리 주석
* 변수에 값 저장하기
  * String
  ```javascript
  const what = "Nicolas"
  const want = "595959"
  ```
  * Boolean
  ```javascript
  const wat = true;
  ```
  * Number
  ```javascript
  const wat = 666;
  ```  
  * Float
  ```javascript
  const wat = 55.1;
  ```    
### 변수명
스페이스 대신에 대문자를 써준다. 점이나 / 등 이상한 문자로 시작하면 안된다.
ex)lowerOfWeek 
### 데이터를 정렬하는 방법
### 1.Array
```javascript
const mon = "Mon";
const tue = "Tue";
const wed = "Wed";
const thu = "Thu";
const fri = "Fri";
console.log(mon, tue, wed, thu, fri);
```
그러나 이것은 효과적이지 않다 => 데이터를 Array로 정렬할 수 있다.
```javascript
const daysOfWeek = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
console.log(daysOfWeek)
console.log(daysOfWeek[2])
```
DB에서 가져온 리스트 데이터라면 Array선택  
데이터를 저장하는 곳, 리스트를 같이 저장한다.  
브라켓을 앞뒤로 써준다. [,]  
ex)요일 저장  
### 2.Object
데이터를 합쳐서 만들어야 하고 많은 사람들을 Array로 만들어야 한다면 Object선택(Object안에 Array를 넣을 수 있음)  
컬러브라켓을 앞뒤로 써준다. {,}  
각 라벨에 데이터를 저장할 수 있다.  
```javascript
const nicoInfo = {
  name:"Nico",
  age:33,
  gender:"Male",
  isHandsome:true,
  favMovies:["Along the gods", "LOTR", "Oldboy"],
  favFood: [
    {
      name:"Kimchi", fatty:false
    },
    {
      name:"Cheeseburger", fatty:true
    }
  ]
}
console.log(nicoInfo.favFood);
```
nicoInfo의 속성은 변경할 수 있지만 nicoInfo자체는 변경할 수 없다.  
★콤바를 넣는 것을 반드시 기억하자!  
※ js가 실행되지 않아도 html,css는 실행된다.

## 3일차
### console
console도 객체임을 확인할 수 있다.  
console안에 있는 함수를 내장 함수라 한다.  
### 함수
내가 가져가 쓸 수 있는 한조각의 코드  
```javascript
function sayHello(name, age){
 console.log('Hello', name, "you have", age, "years of age.");
}
sayHello("Nicolas", 15);
console.log("Hi!");
```
함수는 인자를 받는다. 인자는 변수이고 함수안에서 사용할 이름으로 받는다.  
함수에게 외부에 있는 데이터를 주는 방법이다.  
console.log의 인자는 무수히 많다.  
### 백틱을 사용한 console.log
```javascript
function sayHello(name, age){
  return console.log(`Hello ${name} you are ${age} years old`)
}
const greetNicolas = sayHello("Nicolas", 14);
console.log(greetNicolas);
```
greetNicolas는 sayHello 함수의 리턴값(실행된 결과값)이다.  
```javascript
const calculator = {
  plus: function(a, b){
    return a + b;
  }
}
const plus = calculator.plus(5, 5);
console.log(plus);
```
객체에 함수를 넣어서 사용할 수 있다.
### DOM(Documnet Object Model)
자바스크립트는 HTML에 있는 모든 요소를 가져와서 객체로 바꾼다. => DOM객체 사용
우리가 사용하는 모든 함수는 DOM형태로 변경 가능하다.  
```javascript
const title =document.getElementById("title");
console.log(tilte);
title.innerHTML = "Hi! From JS"
```

querySelector은 노드의 첫번째 자식을 찾아 반환한다.
```javascript
const title = document.querySelector("#title");
title.innerHTML = "Hi! From JS";
title.style.color="red";
document.title = "I own you now";
```
### 이벤트
이벤트를 다룰때 마다 자바스크립트는 자동적으로 함수를 객체에 붙인다.  
event객체는 이벤트 리스너가 호출될 때 인수로 전달되며 해당 타입의 이벤트에 대한 상세 정보를 저장한다.  
```javascript
const title = document.querySelector("#title");
title.innerHTML='Hi! from JS';
function handleClick(event){
    title.style.color = 'red';
    console.log(event)
}
title.addEventListener("click", handleClick);
```

