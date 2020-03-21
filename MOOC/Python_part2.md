# [MOOC - Python 프로그래밍 Ⅱ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC106+P2001/about)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/Python_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용(파이썬 프로그래밍)하여 해결하는 능력을 향상하는 것을 목표로 한다.  

# 목차
* [Ⅴ. 제어 문장 2]()  
  * [반복문]()
  * [반복문 실습]()

  
# Ⅴ. 제어 문장  
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







