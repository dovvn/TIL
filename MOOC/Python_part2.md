# [MOOC - Python 프로그래밍 Ⅱ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC106+P2001/about)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/Python_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용(파이썬 프로그래밍)하여 해결하는 능력을 향상하는 것을 목표로 한다.  

# 목차
* [Ⅴ. 제어 문장 2](#ⅴ-제어-문장-2)  
  * [반복문](#week-5-1-반복문-for-while)
  * [반복문 실습](#week-5-2-반복문-실습)
* [Ⅵ. 함수와 모듈](#ⅵ-함수와-모듈)
  * [함수 개념](#week-6-1-함수-개념)
  * [함수 실습](#week-6-2-함수-실습)
* [Ⅶ. 데이터 구조](#ⅶ-데이터-구조)
  * [리스트](#week-7-1-리스트)
  * [데이터 구조](#week-7-2-데이터-구조)
* [Ⅷ. 파이썬과 인공지능](#ⅷ-파이썬과-인공지능)
  * [파이썬과 인공지능](#4차-산업-혁명)

# Ⅴ. 제어 문장 2  
# WEEK 5-1 반복문 (for, while)
## for
* 반복적이고 지루한 작업은 컴퓨터를 이용하여 자동화
* 리스트(데이터들의 목록)나 튜플(불변한 순서가 있는 객체의 집합), 문자열의 첫번째 요소부터 마지막 요소까지 차례로 변수에 대입되어 "수행할 문장1", "수행할 문장2" 드잉 수행됨
```python
for 변수 in 리스트(또는 튜플, 문자열):
    수행할 문장1
    수행할 문장2
    ...
```
* 예제
```python
for x in range(5): #range()함수는 지정된 범위의 값을 반환
    print("hello")
```
* range()함수
  * range([start, ] stop [,step])
  * range(start,stop)와 같이 호출하면 start부터 시작해서 (stop-1)까지의 정수가 생성
  * stop은 포함되지 않음
  * stop부터 stop-1까지 step의 간격으로 정수들을 생성
  * start와 step이 대괄호로 싸여져 있는데 이는 생략할 수 있다는 의미
  * range(10)하면 0부터 9까지의 정수가 생성
  * 예제 1
  ```python
  sum = 0
  for x in range(10) : #0~9
      sum = sum + x
  print(sum)
  ```
  * 예제 2
  ```python
  sum = 0
  for x in range(1,11,1) : #1~10
     sum = sum + x
  print(sum)
  ```
* 데이터 구조: 리스트(데이터들의 목록)
  * 예제1
  ```python
  for x in [0,1,2,3,4,5,6,7,8,9] :
    print(x, end=" ") # end: 옆으로 한줄로 출력할 수 있도록 도와줌
  ```
  * 예제2
  ```
  for name in ["포닉스", "넙죽이", "눈송이", "독수리"] :
    print("안녕! "+name)
  ```
* 문자열 반복
  * 문자열도 시퀀스의 일부분
  * 문자열을 대상으로 반복문을 만들 수 있음
  ```python
  for c in "abcdef" :
    print(c, end=" ")
  ```
* While
  * 조건의 결과(참 또는 거짓)에 따라 특정 부분의 처리를 반복 실행하는 제어 문장
  * 조건이 참인 동안에 while문 아래에 속한 문장 반복 수행
  ```python
  while 조건문:
      수행할 문장1
      수행할 문장2
      수행할 문장3
      수행할 문장4
      ...
  ```
  * 예제
  ```python
  i = 0
  while i < 5 :
     print("hello python")
     i=i+1
  print("반복 종료")
  ```
## 분기문(Jump Statement)
* 반복문 탈출하는 break문
```python
for i in range(1,100) : #1~99
    print("for문을 %d번 실행" %i)
    break
```
실행결과  
![break](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_break.PNG)
* 반복문으로 다시 돌아가는 continue문
  * continue문을 만나면 무조건 블록의 남은 부분은 건너뛰고 반복문의 처음으로 돌아감
```python
hap, i = 0,0
for i in range(1,101) :
    if i % 3 == 0 :
        continue
    hap += i
print("1~100까지의 함계(3의 배수 제외): %d" %hap)
```
실행결과  
![continue](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_continue.PNG)

# WEEK 5-2 반복문 실습
## 1부터 사용자가 입력한 수 n까지 더해서 (1+2+3+...+n)을 계산하는 프로그램 작성(for문 사용)
```python
sum = 0
limit = int(input("어디까지 계산할까요: "))
for i in range(1, limit+1) :
    sum += i
print("1부터 ", limit, "가지의 정수의 합= ",sum)
```
실행 결과  
![sumofinteger](https://github.com/jdaun/TIL/blob/master/MOOC/img/sumex_python.PNG)  

## 팩토리얼 계산
* for문을 이용하여 팩토리얼 계산
* 팩토리얼 n!은 1부터 n까지의 정수를 모두 곱한 것을 의미 n! = 1x2x3x...x(n-1)xn이다.  
```python
fact = 1.0
n = int(input("정수를 입력하시오: "))
for i in range(1, n+1) :
    fact = fact * i;
print(n,"!은 ", fact, "이다.")
```
실행결과  
![팩토리얼예제](https://github.com/jdaun/TIL/blob/master/MOOC/img/factorial_ex.PNG)

## 자리수의 합
* 정수 안의 각 자리수의 합을 계산하는 프로그램을 작성
* 예를 들어서 1234라면 (1+2+3+4)를 계산

실행결과  
![자리수의 합](https://github.com/jdaun/TIL/blob/master/MOOC/img/sumnmb_python.PNG)

## 숫자 맞추기 게임
* 컴퓨터가 선택한 숫자를 사용자가 맞추는 게임
* 입력한 숫자가 선택한 숫자보다 높은 수인지 낮은 수 인지 정보 제공
* 시도 횟수 제공
```python
import random

tries = 0
number = random.randint(1, 100)
# print("number값: ",number)

print("1부터 100사이의 숫자를 맞추시오")

while tries < 10:
    guess = int(input("숫자를 입력하세요: "))
    print("입력값: ",guess)
    tries = tries + 1
    if guess < number:
        print("더 높게 입력하세요")
    elif guess > number:
        print("더 낮게 입력하세요")
    else:
        break
    
if guess == number:
        print("축하합니다. 시도 횟수=", tries)
else:
    print("정답은", number)
```
실행 결과  
![숫자맞추기](https://github.com/jdaun/TIL/blob/master/MOOC/img/number_python.PNG)

## 커피 자판기
```python
coffee = 10
money = 300
while money:
    print("돈을 받았으니 커피를 줍니다.")
    coffee = coffee - 1
    print("남은 커피의 양은 %d개 입니다" %coffee)
    if not coffee: 
        print("커피가 다 떨어졌습니다. 판매를 중지합니다.")
        break
```
실행 결과  
![커피자판기](https://github.com/jdaun/TIL/blob/master/MOOC/img/coffeegame_python.PNG)

# Ⅵ. 함수와 모듈
# WEEK 6-1 함수 개념
## 함수
* 독립적으로 수행하는 프로그램 단위로 특정 작업을 수행하는 명령어들의 모음에 이름을 붙인 것
## 함수 정의
* def로 시작하고 클론(:)으로 끝냄
* 함수의 시작과 끝은 코드의 들여쓰기로 구분
* 시작과 끝을 명시해 줄 필요가 없음
```python
def 함수이름 (입력 인수) :
    수행할 문장
    ...
    return 반환값
```
## 함수 정의 문법
```python
def 함수이름 (Arguemnt list ...):
    수행문(statements)
    return <반환값>
```
* 간단한 함수 선언해 보기
  * 입력 받은 2개의 매개변수(인수)를 서로 더한 값을 리턴
```python
def add(a, b):
    return a+b
```
쉘 환경에서 add (10,10) 호출하면 20이 출력된다.  

## 함수 매개변수와 반환 값
* 입력 값과 반환 값이 없는 함수
```python
def say():
    print("hello")
```
* 입력 값은 없고 반환 값이 있는 함수
```python
def say():
   return("hello")
```

## 함수 작성 예시(1)
* 정수의 거듭제곱값을 계산하여 반환하는 함수 작성(**연산자 사용가능)
```python
def power(x, y):
    result = 1
    for i in range(y):
        result = result * x
    return result

print(power(10, 2))
```

## 함수를 이용할 때 주의할 점
* 파이썬 인터프리터는 함수가 정의되면 함수 안의 문장들은 실행하지 않음
* 함수 정의가 아닌 문장들은 즉시 실행  

## 함수 작성 예시(2)
* 정수의 거듭제곱값을 계산하여 반환하는 함수 작성(**연산자 사용가능)
* main() 함수 호출 활용
```python
def main():
    print(power(10,2))

def power(x, y):
    result = 1
    for i in range(y):
        result = result * x
    return result

main()
```

# WEEK 6-2 함수 실습
## 성적처리를 위한 주요 함수 만들기
* 성적 처리 특성 분석
  * 총점계산하기 add()
  * 총점을 사용하여 평균 계산
  * 총점을 반영하여 성적순으로 정렬
  * 정렬을 위해서 두 변수의 값을 서로 바꾸는 함수 필요(swap()) => 파이썬에서는 여러 값 리턴 가능

```python
# 함수
def add(a,b):
    return a+b

def swap(a,b):
    a,b = b,a
    return a,b

# 시작코드
a = int(input("정수1 입력: "))
b = int(input("정수2 입력: "))
sum = add(a,b)
average = sum/2
print("두 수의 합: ", sum)
print("두 수의 평균: ", average)
a,b = swap(a,b)
print("두 수의 교환: ", a, b)
```

실행 결과  
![함수실습](https://github.com/jdaun/TIL/blob/master/MOOC/img/ex_function.PNG)


# Ⅶ. 데이터 구조 
# WEEK 7-1 리스트
## 리스트란?
* 여러 개의 데이터가 저장되어 있는 장소
* 선언
리스트이름 = [값1, 값2, 값3]  
scores = [32, 56, 64, 72, 12, 37, 98, 77, 59, 69]
* 리스트를 여러 개의 데이터를 하나의 이름을 관리할 수 있는 데이터 구조
* ★서로 다른★ 데이터 타입의 데이터를 하나의 리스트 이름으로 관리 가능
* 문자열을 원소로 가지는 예제  
```python
fruit = ["banana", "apple", "cherry"]
```
* 숫자를 원소로 가지는 예제
```python
score = [70, 99, 25, 100]

* Empty list
```python
empty_list = []
```
## 리스트 원소에 접근 하기
* 인덱스
  * 원소가 배열된 순서를 나타냄. (0번 부터 시작)
  * 인덱스를 이용하여 원소에 접근할 수 있음
  >>> season[1]
## 리스트와 연산자
* in: list의 element인가를 결정하는 연산자
* not in: list의 element가 아닌 element를 결정하는 연산자
```python
fruit = ["banana", "apple", "cherry"]
"apple" in fruit #true
```
## 리스트 순회하기
```python
scores = [32, 56, 64, 72, 12, 37]
for element in scores:
    print(element, end=' ') # 32 56 64 72 37
```
## 리스트 사용가능 함수
![리스트 사용가능 함수](https://github.com/jdaun/TIL/blob/master/MOOC/img/list_function.PNG)
## 예제: 성적 처리 프로그램
* 학생들의 성적을 받아서 리스트에 저장
* 성적의 평균을 구하고 80점 이상 성적을 받은 학생의 숫자를 계산하여 출력
```python
students = 5

scores = []
scoreSum = 0

for i in range(students):
    value = int(input("성적을 입력하세요: "))
    scores.append(value) #리스트에 값을 추가
    scoreSum += value

scoreAvg = scoreSum / len(scores)
highScoreStudents = 0
for i in range(len(scores)):
    if scores[i] >= 80:
        highScoreStudents += 1

print("성적 평균은", scoreAvg, "입니다")
print("80점 이상 성적을 받은 학생은", highScoreStudents, "명입니다.")
```
실행 결과  
![성적처리프로그램](https://github.com/jdaun/TIL/blob/master/MOOC/img/ex_list1.PNG)

## 문자열 처리 프로그램
* 리스트는 문자열도 저장 가능
* 학생들의 이름을 저장하였다가 출력하는 프로그램을 작성
```python
Names = []
while True:
    name = input("학생 이름을 입력하세요: ")
    if name == "" :
        break
    Names.append(name)

print("학생 이름:")
for name in Names:
    print(name, end=", ")
```

![실행결과](https://github.com/jdaun/TIL/blob/master/MOOC/img/list_ex2.PNG)

# WEEK 7-2 데이터 구조
## 데이터구조란?
* 프로그램에서 자료들을 저장하는 여러가지 구조들이 있다. 이를 자료구조라한다.
* 파이썬에는 리스트, 튜플, 딕셔너리, 문자열 등 다양한 데이터 구조를 기본으로 사용할 수 있도록 제공한다.
## 리스트 예제: 연락처 관리 프로그램
```python
menu = 0
friends = []
while menu != 9:
    print("----------------");
    print("1. 친구 리스트 출력")
    print("2. 친구추가")
    print("3. 친구삭제")
    print("4. 이름변경")
    print("9. 종료 ")
    menu = int(input("메뉴를 선택하시오: "))
    if menu == 1:
        print(friends)
    elif menu == 2:
        name = input("이름을 입력하시오: ")
        friends.append(name)
    elif menu == 3:
        del_name = input("삭제하고 싶은 이름을 입력하시오: ")
        if del_name in friends:
            friends.remove(del_name)
        else:
            print("이름이 발견되지 않았음")
    elif menu == 4:
        old_name = input("변경하고 싶은 이름을 입력하시오: ")
        if old_name in friends:
            index = friends.index(old_name)
            new_name = input("새로운 이름을 입력하세요")
            friends[index] = new_name
        else:
            print("이름이 발견되지 않았음")
        
```
![리스트예제](https://github.com/jdaun/TIL/blob/master/MOOC/img/datalist_python.PNG)
## 튜플
* 튜플(tuple)은 값을 변경할 수 없는 리스트
* 튜플 = (항목1, 항목2, ..., 항목n)
```python
colors = ("red, "yello" blue")
t1 = (1, 2, 3, 4, 5)
t = numbers + colors # (1, 2, 3, 4, 5, "red, "yello" blue")
```
## 딕셔너리
* 딕셔너리는 키(key)와 값(value)의 쌍을 저장할 수 있는 객체
* 딕셔너리 = {키1:값1, 키2:값2, 키3:값3...}
```python
contacts = {'kim' : '01012345678', 'Park':'0123456789'}
contacts['kim'] # '01012345678
contacts.get('Kim') # '01012345678

if "Kim" in contacts:
    print("키가 딕셔너리에 있음")
```
## 항목 순회하기
```python
scores = {'Korean' : 80, 'Math' : 90, 'English' : 80}
for item in scores.items():
    print(item)
# 출력 결과
# ('Korean', 80)
# ('Math', 90)
# ('English', 80)
```
## 문자열
* 문자열은 문자들의 시퀀스로 정의
* 글자들이 실(string)로 묶여 있는 것이 문자열

```python
s1 = str("Hello")
s2 = "world"
s3 = s1 + s2 #Helloworld
```
## 개별 문자 접근하기
```python
word = 'abcdef'
word[0] #a
```
## 슬라이싱
```python
word = 'Python'
word[0:2] #0부터 2보다 작을때 까지 => Py
word[2:5] # tho
```
## in연산자와 not in 연산자
```python
s = "Love will find a way."
"Love" in s #True
```

```python
s = input("문자열을 입력하세요")
if 'c' in s:
    print('c가 포함되어 있음')
else:
    print('포함되어 있지 않음')
```

# Ⅷ. 파이썬과 인공지능
## WEEK 8-1 파이썬과 인공지능
## 4차 산업 혁명
* 3차 산업 혁명의 컴퓨터, 인터넷 + AI,SW와 빅데이터IoT, 클라우드 => 제품 생산의 지능화! 고객 맞춤형 생산! ex.에어비앤비, 우버
* 지능화, 다양한 분야의 융합
* 클라우드 슈밥 - 제 4차 산업혁명책 추천
* 왜 일어났을까?
  * 시작혁명의 원인이 인류의 변화로 보는 관점
  * 호모 포노 사피엔스: 스마트폰을 자유롭게 사용하는 신인류
* 글로벌 10대 기업이 제조업에서 SW관련 회사로 변화하는 중이다.
* 신인류가 선택할 미래의 기업은?
  * 유니콘 벤처: 기억 가치가 100억 달러 이상인 신생 벤처기업
* 인공지능
  * 인공지능(AI)
    컴퓨터가 사람처럼 생각하고, 판단하게 만드는 기술  
  * 머신러닝(ML)
    인공지능의 한 분야, 인간의 학습능력과 같은 기능을 컴퓨터에 부여하기 위한 기술  
  * 딥러닝(DL)
    인공 신경망을 기반으로 한 머신러닝 방법론 중 하나  
    빅데이터를 기반으로 스스로 학습하여, 판단하는 기술  
