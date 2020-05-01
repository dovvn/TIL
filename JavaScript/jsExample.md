# JavaScript 실습  
이 문서는 자바스크립트 실습코드 기록용으로 작성한다.  

# 목차
* [웹 게임 자바스크립트](#웹-게임-자바스크립트)  
  * [끝말잇기 게임](#끝말잇기-게임)  
  * [구구단 게임](#구구단-게임)  
  * [비동기 & 숫자야구 순서도](#비동기-&-숫자야구-순서도)

# 웹 게임 자바스크립트  
출처 - [웹 게임을 만들며 배우는 JavaScript(자바스크립트)](http://bitly.kr/5yc1u9zX5)  
## 끝말잇기 게임  
컴퓨터가 제시한 단어를 시작으로 단어의 끝 문자가 다음 단어의 첫 문자와 이어지도록 끝말잇기 하는 간단한 게임

끝말잇기.html  
```javascript
<!DOCTYPE html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>끝말잇기</title>
</head>
<body>
    <!-- <div>토마토</div>
    <form>
        <input type="text" />
        <button>등록</button>
    </form>
    <div>딩동댕</div> -->
    <script src = "끝말잇기.js"></script>
</body>
</html>
```

끝말잇기.js  
```javascript  
// document 윈도우 안에 들어있는 브라우저가 지원하는 객체  
// html태그를 가리침, html태그를 javascript로 번역해주는  
// 통역사 같은 역할. dom객체  

var 바디 = document.body;  
var 단어 = document.createElement('div'); //태그 생성  
단어.textContent = '토마토'; //태그안에 들어가는 글자  
document.body.append(단어); //body에 추가  
var 폼 = document.createElement('form');  
document.body.append(폼);  
var 입력창 = document.createElement('input');  
폼.append(입력창);
var 버튼 = document.createElement('button');
버튼.textContent = '입력';
폼.append(버튼);
var 결과창 = document.createElement('div');
document.body.append(결과창);

//form은 enter 가능, enter치면 새로고침(default)
폼.addEventListener('submit', function 콜백함수(이벤트) { //익명함수: 함수이름x
    이벤트.preventDefault(); //enter시 새로고침x
    if(단어.textContent[단어.textContent.length-1] == 입력창.value[0]){ //입력착.value = 초밥
        결과창.textContent = '딩동댕';
        단어.textContent = 입력창.value;
        입력창.value='';
        입력창.focuse();
    }else{
        결과창.textContent = '땡';
        입력창.value='';
        입력창.focuse();
    }
});
```

## 구구단 게임
컴퓨터가 계산한 두개의 난수값의 곱을 사용자가 맞춰보는 간단한 게임  
구구단.html  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- <div></div>
    <form>
        <input type="text"/>
        <button>등록</button>
    </form>
    <div></div> -->
    <script src="구구단.js"></script>
</body>
</html>
```

구구단.js  
```javascript
var 숫자1 = Math.ceil(Math.random() * 9);
var 숫자2 = Math.ceil(Math.random() * 9);
var 결과 = 숫자1 * 숫자2;

var 바디 = document.body;
var 단어 = document.createElement('div');
단어.textContent = String(숫자1) + ' x ' + String(숫자2)+ '는?';
document.body.append(단어);
var 폼 = document.createElement('form');
document.body.append(폼);
var 입력창 = document.createElement('input');
폼.append(입력창);
var 버튼 = document.createElement('button');
버튼.textContent = '입력';
폼.append(버튼);
var 결과창 = document.createElement('div');
document.body.append(결과창);

폼.addEventListener('submit', function 콜백함수 (e){
    e.preventDefault();
    console.log(결과, Number(입력창.value));
    if(결과 == Number(입력창.value)){
        결과창.textContent = '딩동댕';
        숫자1 = Math.ceil(Math.random() * 9);
        숫자2 = Math.ceil(Math.random() * 9);
        결과 = 숫자1 * 숫자2;
        단어.textContent = String(숫자1) + ' x ' + String(숫자2)+ '는?';
        입력창.value='';
        입력창.focus();
    }else{
        결과창.textContent = '땡';
        숫자1 = Math.ceil(Math.random() * 9);
        숫자2 = Math.ceil(Math.random() * 9);
        입력창.value='';
        입력창.focus();
    }
});
```
# 비동기 & 숫자야구 순서도
컴퓨터가 만든 임의의 숫자 4개와 사용자가 입력한 숫자 4개가 모두 일치하면 홈런을 출력한다.
단, 숫자가 모두 일치하지는 않지만 각 숫자가 같은 자리이면 그 수만큼 '스트라이크', 같은 자리는 아니지면 숫자가 겹치면 그 수만큼 '볼'을 출력한다. 답을 4번 넘게 틀릴 경우 다음 게임으로 넘어간다. 

push: 마지막에 추가  
pop: 마지막 것 뽑기  
unshift: 처음에 추가  
shift: 처음 것 뽑기   
splice(위치, 개수): 위치로부터 개수만큼 배열에서 뽑음  
새로고침: submit의 기본 동작, 이벤트를 끌려면 preventDefault()사용  
문자.spilit(구분자) -> 배열   
배열.join(구분자) -> 문자  
배열.indexOf(값) -> 값의 위치 알 수 있음, 없으면 -1  

숫자야구.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script src="숫자야구.js"></script>
</body>
</html>
```

숫자야구.js  
```javascript
var 바디 = document.body;

var 숫자후보 = [1,2,3,4,5,6,7,8,9];
var 숫자배열 = [];
for(var i=0; i<4; i++){
    var 뽑은것 = 숫자후보.splice(Math.floor(Math.random()* (9-i)), 1)[0];
    숫자배열.push(뽑은것);
}
console.log(숫자배열);

var 결과 = document.createElement('h1');
바디.append(결과);
var 폼 = document.createElement('form');
document.body.append(폼);
var 입력창 = document.createElement('input');
입력창.type = 'number';
입력창.maxLength = 4;
폼.append(입력창);
var 버튼 = document.createElement('button');
버튼.textContent = '입력!';
폼.append(버튼);

var 틀린횟수 = 0;
폼.addEventListener('submit', function 비동기(이벤트){
    이벤트.preventDefault();
    var 답 = 입력창.value;
    console.log(답, 숫자배열, 답==숫자배열.join(''));
    if( 답 == 숫자배열.join('')) { //답이 맞으면
        결과.textContent = '홈런';
        입력창.value='';
        입력창.focus();
        숫자후보 = [1,2,3,4,5,6,7,8,9];
        숫자배열 = [];
        for( i=0; i<4; i++){
        var 뽑은것 = 숫자후보.splice(Math.floor(Math.random()* (9-i)), 1)[0];
        숫자배열.push(뽑은것);
        }
        console.log(숫자배열);
        틀린횟수 = 0;
    }else{ //답이 틀리면
        var 답배열 = 답.split('');
        var 스트라이크 = 0;
        var 볼 = 0;
        틀린횟수 ++;
        console.log('틀린횟수 '+ 틀린횟수);
        if(틀린횟수 > 4){
            결과.textContent = '4번 넘게 틀려서 실패! 답은' + 숫자배열.join(',') + '였습니다!';
            입력창.value='';
            입력창.focus();
            숫자후보 = [1,2,3,4,5,6,7,8,9];
            숫자배열 = [];
            for(i=0; i<4; i++){
            var 뽑은것 = 숫자후보.splice(Math.floor(Math.random() * (9-i)), 1)[0];
            숫자배열.push(뽑은것);
            }

            틀린횟수 = 0;
        } else{
            for(var i=0; i<4; i++){
                if(Number(답배열[i]) == 숫자배열[i]){ //같은 자리인지 확인
                    스트라이크++;
                }else if(숫자배열.indexOf(Number(답배열[i])) > -1 ){ //같은 자리는 아니지만, 숫자가 겹치는지 확인
                    볼++;
                }
            }
            결과.textContent = 스트라이크+'스트라이크 ' + 볼 +' 볼 입니다.';
            입력창.value='';
            입력창.focus();
        }
    }
});
```
