# 자바스크립트(JavaScript) 이론
[tcp school](http://tcpschool.com/javascript/js_intro_basic) 참고  
이 문서는 필요한 개념만을 간략히 작성하였으며 중간에 새로 알게 된 개념이 추가 될 확률이 높다.

오래 전 자바스크립트를 독학하였지만 중간에 다른 언어를 공부하면서 개념 공부가 필요해졌다.  
최대한 빠른 시간내에 개념을 속독한 후, 작은 실습부터 시작하면서 스킬을 늘리도록 한다.  

# 목차
* [JavaScript란?](#javascript란)
* JavaScript의 특징(#javascript의-특징)
* JavaScript의 출력(#javascript의-출력)
* JavaScript의 적용(#javascript의-적용)
* 기본 타입(#기본-타입)  


## JavaScript란?
자바스크립트(JavaScript)란 객체 기반의 스크립트 언어이다.
Html는 웹의 정적인 부분, CSS는 웹의 디자인, JavaScript는 웹의 동적인 부분을 구현한다.
주로 웹브라우저에서 사용되며, Node.js와 같은 프레임워크를 통해 서버 측 프로그래밍에서도 사용가능하다.  


## JavaScript의 특징
* 자바스크립트는 객체 기반의 스크립트 언어이다.
* 자바스크립트는 동적이며, 타입을 명시할 필요가 없는 인터프리터 언어이다.
  * 인터프리터언어는 컴파일 작업을 거치지 않고, 번역과 동시에 코드를 바로 실행한다.
* 자바스크립트는 객체 지향형 프로그래밍과 함수형 프로그래밍을 모두 표현할 수 있다.


## JavaScript의 출력  
자바스크립트는 여러 방법을 통해 결과물을 HTML페이지에 출력할 수 있다.

* window.alert() 메소드
  별도의 대화 상자를 띄워 사용자에게 데이터를 전달한다.
* HTML DOM 요소를 이용한 innerHTML 프로퍼티
  예를 들어document객체의 getElementByID()나 getElementByTagName() 등의 메소드를 사용하여 HTML 요소를 선택한다.  
  그리고 innerHTML 프로퍼티를 이용하면 선택된 HTML 요소의 내용(content)이나 속성(attribute)값 등을 손쉽게 변경할 수 있다.  
* document.write() 메소드
  웹 페이지가 로딩될 때 실행되면, 웹 페이지에 가장 먼저 데이터를 출력한다.  
  따라서 document.write()메소드는 대부분 테스트나 디버깅을 위해 사용된다.
* console.log() 메소드
  웹 브라우저의 콘솔을 통해 데이터를 출력한다.
  대부분 주요 웹 브라우저의 F12를 누른 후, 메뉴에서 콘솔을 클릭하면 콘솔 화면을 사용할 수 있다.  
  
  
## JavaScript의 적용
HTML 문서에 자바스크립트 코드를 적용하는 방법은 다음과 같다.
1. 내부 자바스크립트 코드로 적용
     <script>태그를 사용하여 HTML 문서 안에 삽입할 수 있다.
     이 때, 삽입할 수 있는 위치는 head태그, body태그이다.  
``` html
<script>
    document.getElementById("text").innerHTML = "여러분을 환영합니다!";
</script>
```
 2. 외부 자바스크립트 코드로 적용
 외부에 작성된 자바스크립트 파일(확장자 .js)를 삽입할 수 있다.
 해당 js파일은 적용하고 싶은 모든 웹페이지에 <script>태그를 사용해 외부 자바스크립트 파일을 포함시킨다.
 ``` html
<head>
    <meta charset="UTF-8">
    <title>JavaScript Apply</title>
    <script src="/examples/media/example.js"></script>
</head>
```
 외부 js파일을 삽입하면 웹의 정적인 부분(HTML)과 웹의 동적인 부분(JavaScript)이 분리되어 코드를 각각 읽기 편해지고, 유지보수도 쉬워진다.  
 또한, 외부 js파일을 웹 브라우저가 미리 읽어올 수 있어 웹페이지의 로딩 속도가 빨라진다.
 
 
 ## 기본 타입  
* 숫자(number)
  다른 언어와 달리 정수와 실수를 따로 구분하지 않고, 모든 수를 하나로만 표현한다.
  매우 큰 수, 매우 작은 수는 e표기법을 사용한다.  
 ``` javascript
var firstNum = 10;     // 소수점을 사용하지 않은 표현
var secondNum = 10.00; // 소수점을 사용한 표현
var thirdNum = 10e6;   // 10000000
var fourthNum = 10e-6; // 0.00001
```

* 문자열(String)
  큰따옴표("")나 작은따옴포('')로 둘러싸인 문자의 집합  
 ``` javascript
var firstStr = "이것도 문자열입니다.";      // 큰따옴표를 사용한 문자열
var secondStr = '이것도 문자열입니다.';     // 작은따옴표를 사용한 문자열
var thirdStr = "나의 이름은 '홍길동'이야."  // 작은따옴표는 큰따옴표로 둘러싸인 문자열에만 포함될 수 있음.
var fourthStr = '나의 이름은 "홍길동"이야.' // 큰따옴표는 작은따옴표로 둘러싸인 문자열에만 포함될 수 있음.
```
  이 때, 숫자와 문자열을 더할 수도 있다.
 ``` javascript
var num = 10;
var str = "JavaScript";
document.getElementById("result").innerHTML = (num + str); // 10JavaScript
```

* 불리언(boolean)
  참(true)과 거짓(blue)을 표현한다.
 ``` javascript
var firstNum = 10;
var secondNum = 11;
document.getElementById("result").innerHTML = (firstNum == secondNum); //false
``` 

* 심볼(symbol): ECMAScript6부터 제공
  유일하고 변경할 수 없는 타입, 객체의 프로퍼티를 위한 식별자로 사용할 수 있다.
  단, 익스플로러에서 지원하지 않는다.  
 ``` javascript
var sym = Symbol("javascript");  // symbol 타입
var symObj = Object(sym);        // object 타입
```

* null과 undefined
  null은 object타입이며, 아직 '값'이 정해지지 않은 것을 의미한다.
  undefined는 null과 달리 '타입'이 정해지지 않은 것을 의미한다. 초기화되지 않은 변수나 존재하지 않는 값에 접근할 때 반환된다.  
 ``` javascript
var num; //초기화되지 않았으므로 undefined값을 반환
var str = null; //object타입의 null값
typeof secondNum; //정의되지 않은 변수에 접근하면 undefined 값을 반환

null == undefined; //true
null === undefined; //false 타입을 제외하면 같은 의미지만, 타입이 다르므로 일치하지 않는다.
```
 
* 객체(object)
  자바스크립트의 기본 타입은 객체이다.
  객체는 여러 프로퍼티(propert)나 메소드(method)를 묶어놓은 일종의 집합체이다.
 ``` javascript
var dog = { name:"해피", age:3};
document.getElemntById("result").innerHTML="강아지 이름"+dog.name+", 나이"+dog.age+"살";
```
자세한 내용은 자바스크립트 객체에 기록해두었다.


## 타입 변환(Type Conversion)
자바스크립트의 변수는 타입이 정해져 있지 않으므로 같은 변수에 다른 타입의 값을 다시 대입할 수 있다.

 * 묵시적 타입 변환(implicit type conversion)
 * 명시적 타입 변환(explicit type conversion)
  
