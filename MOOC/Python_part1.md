# [MOOC - Python 프로그래밍 Ⅰ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC105+P2001/course/)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용하여 일상 생활에 주어진 문제를 해결할 수 있도록 프로그래밍 기본 원리와 개념을 이해한다.  
문제 해결을 위해 C 언어로 프로그래밍 언어의 기본 구조와 문법을 알고, 그 문법으로 해결할 수 있는 다양한 일상 생활의 문제를 예제를 통해 학습한다.  

# 목차
* [Ⅰ. 문제 해결](#ⅰ-문제-해결)  
  * [컴퓨팅 사고력과 문제해결](#week-1-1-컴퓨팅-사고력과-문제해결)
  * [파이썬 개발환경](#week-1-2-파이썬-개발환경)
* [Ⅱ. 파이썬 개요](#ⅱ-파이썬-개요)
  * [파이썬 개요](#week-2-1-파이썬-개요)
  * [변수와 메모리](#week-2-2-변수와-메모리)
  * [입출력함수](#week-2-3-입출력함수)
* [Ⅲ. 연산자]()  
  * [연산자](#week-3-1-연산자)
  * [연산자 실습](#week-3-2-연산자-실습)
* [Ⅳ. 제어 문장 1]()
  * [조건문(if)]()
  * [조건문 실습]()
  
# Ⅰ. 문제 해결  
# WEEK 1-1 컴퓨팅 사고력과 문제해결
이전에 학습한 CT1과 내용이 비슷하므로 생략. [CT1 문서](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md#week-1-1-%EB%AC%B8%EC%A0%9C-%ED%95%B4%EA%B2%B0problem-solving)에서 확인할 것.

# WEEK 1-2 파이썬 개발환경
## 파이썬 설치
먼저, 최신 버전 파이썬을 [다운로드](https://www.python.org/downloads/) 받는다.

## 파이썬 실행 환경
* 파이썬 IDLE(Integrated Development and Learning Environment)
  * 파이썬을 개발 하기 위한 통합 개발 환경 의미
* IDLE는 두 가지 모드로 사용 가능
  * 대화형 파이썬 쉘(Python Shell)과 편집기 모드로 사용 가능
  * 1. 짧고 간단한 예제 코드는 파이썬 쉘을 이용
  * 2. 길고 복잡한 예제 코드는 코드 편집기를 이용
## 1. 파이썬 쉘로 코딩하기  
* IDLE에서 "hello world"를 출력한 모습  

![helloworld](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_helloworld.PNG)  

## 2. 코드 편집기로 코딩하기  
* IDLE창에서 File-New File을 클릭하여 코드 편집기 실행한다. 여기서 바로 코딩 가능하다.  
* 코드 입력후 ctrl+s 파일 저장
* 코드 편집기가 활성화 된 상태에서 F5 버튼 클릭
![코드편집기](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_shell.PNG)

## 다양한 운영체제에서 실행 가능
애플, 윈도우, 라즈페리 파이, 리눅스 등등...  

# Ⅱ. 파이썬 개요  
# WEEK 2-1 파이썬 개요
## 파이선 특징
* 1991년 귀도 반 로섬(Gudi Van Rossum) 발표
  * 플랫폼 독립적
  * 인터프리터 언어
  * 객체 지향
  * 동적 타이핑 언어
  * AI 프로그래밍을 위한 많은 라이브러리 제공
  * 처음 C언어로 구현되었음
## Python구조: Python은 여러 개의 프로그래밍 스타일을 포괄
* 1.절차 지향 프로그래밍
  * 처리해야할 문제의 해결 과정을 큰 문제를 독립적으로 기능별로 나눠서 일련의 순서에 따라서 처리
  * 절차 지향 프로그래밍은 함수가 필수적  
  ![파이썬구조](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_structure.PNG)  
  
* 2.객체 지향 프로그래밍  
  * 관계 있는 데이터와 함수를 하나로 묶어서 선언하는 클래스라는 개념을 도입
  * 클래스는 객체를 생성하는 데이터 타입 역할
  * 객체 지향 개념(상속, 다형성 등)을 활용하여 효율적으로 코드 작성
  * 객체 지향 프로그래밍은 클래스(객체)가 필수적
* 함수형 프로그래밍
  * 절차지향의 경우 일련의 명령을 통해서 변수를 바꿔 가면서 전체적인 프로그램을 동작하게 하지만 함수형 프로그래밍의 경우 기존의 함수와는 다른 수학적인 모델링을 통한 함수의 사용으로 프로그램의 동작 및 예측에 대한 능률을 높여줌
  * 함수형 코드에서는 함수의 출력값은 그 함수에 입력된 인수에만 의존하므로 인수 x에 같은 값을 넣고 함수 f를 호출하면 항상 f(x)라는 결과가 나오므로 프로그래므이 동작을 이해하고 예측하기 쉬움
![파이썬구조2](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_structure2.PNG)

## Python 프로그램 구조
![파이썬구조3](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_structure3.PNG)  

# WEEK 2-2 변수와 메모리
## 변수(variable)
* 변수: 사용할 데이터를 저장하는 공간
* 데이터 타입을 생략하고 변수 선언 가능
```python
a=10; b=20
sum = a + b
print(a, "+", b, "=", sum)
```
* 동적타이핑(dynamic typing)  
  * 런 타임에 구문을 통해 Data Type을 설정한다.  
* Python에서 변수는 객체를 가리키는 ID값을 담고 있는 저장 공간   
  * a,b,c,d라는 변수는 저장공간안에 1,2,3,4라는 상수적 객체에 참조(아이디 값을 갖고있음)한다.  
![python_variable](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_variable.PNG)  
## 변수의 활용
* 파이썬에서 변수의 데이터 형식은 값을 넣는 순간마다 변경될 수 있는 유연한 구조이다.  
![change_change](https://github.com/jdaun/TIL/blob/master/MOOC/img/python_change.PNG)  
* 변수에는 다른 변수의 값도 저장 가능  
* 문자열, 실수도 마찬가지로 자동으로 데이터타입이 변경된다.  
## 변수 실습  
Q. 변수x와 변수y의 값을 서로 바꾸는 프로그램을 작성   
* 방법1  
```python
x = 90
y = 95
print(x,y) # 90 95

temp=x
x=y
y=temp

print(x,y) # 95 90
```

* 방법2  
```python
a = 10
b = 20
a,b = b,a
print(a,b) # 20 10
```

# WEEK 2-3 입출력함수
## input(), print()함수
```python
x = input("첫번째 정수: ")
y = input("두번째 정수: ")
sum = x + y
print("합은 ", sum)
```  
함수 input()을 통해 입력받은 내용의 데이터 타입은 문자열이기 때문에 숫자를 입력하더라도 문자열로 간주되므로 사칙연산이 불가능하다.  

```python
x = int(input("첫 번째 정수: ")) #int로 바꿔서 x에 넣어라
y = int(input("두 전째 정수: "))

sum = x + y
print("합은", sum)
```  

또는 그대로 코드를 작성한 후 나중에 계산 시 int(x)+int(y)로도 구할 수 있다.  

# Ⅲ. 연산자
# WEEK 3-1 연산자
## 연산자의 개념
* 연산자
  * 산술연산자 +, -, *기호와 같이, 이미 정의된 연산을 수행하는 기호나 키워드를 의미
* 연산자는 왜 필요할까?
  * 문제를 해결하는 방법에서 도구(장비)와 같은 역할
* 피연산자
  * 연산에 참여하는 변수나 값
## 1. 산술연산자
=, +, -, *, /, //나누기(몫), &(나머지값), **(제곱)   
```pyton
print(25//10**2+1) # 1
```

* 우선순위
  * 괄호가 가장 우선, 곱셈(또는 나눗셈)이 그 다음, 덧셈(또는 뺄셈)이 가장 마지막으로 수행
  * 덧셈(또는 뺼셈)끼리 나오거나 곱셈(또는 나눗셈)끼리 나오면 왼쪽에서 오른쪽으로 계산이 진행됨
* 문자열과 숫자의 상호 변환
  * 문자열이 int()함수에 의해서 정수로, float()함수에 의해서 실수로 변경
  ```python
  s1, s2, s3 = "100", "100.123", "9999999999999"
  print(int(s1)+1, float(s2)+1, int(s3)+1) # 101 101.123 10000000000000
  ```
* 숫자를 문자열로 변환하기 위해서는 str()함수를 사용
  ```python
  a = 100;
  b = 100.123
  str(a)+'1'; str(b)+'1' # '1001' '100.1231'
  ```
## 2. 대입 연산자
* 변수의 저장 값을 대입하는 =기호가 대입(할당)연산자
## 3. 관계 연산자
* 어떤 것이 큰지, 작은지, 같은지를 비교하는 것, 결과는 참(True)이나 거짓(False)
* 주로 조건문(If)이나 반복문(for, while)에서 사용
* ==, !=, >, <, <=, <=
## 4. 논리연산자
* and, or, not
```python
a=99
(a>100) and (a<200) #False
(a>100) and (a<200) #True
not(a==100) #True
```
# WEEK 3-2 연산자 실습
## 일상 생활 문제 해결: 윤년
* 윤년을 계산하는 방법 조사하기(치윤법)  
1. 기원 연수가 4로 나누어 떨어지는 해는 우선 윤년으로 하고,  
2. 그 중에서 100으로 나누어 떨어지는 해는 평년으로 하며,  
3. 다만 400으로 나누어 떨어지는 해는 다시 윤년으로 정한다.  
* 컴퓨터를 활용하여 계산하는 방법(알고리즘)을 찾기
1. 기원 연수가 4로 나누어 떨어지는 해는 우선 윤년으로 하고,  
(year % 4 == 0)  
2. 그중에서 100으로 나누어 떨어지는 해는 평년으로 하며,  
// 윤년을 구하려면?  
(year % 100 != 0)  
3. 다만 400으로 나누어 떨어지는 해는 다시 윤년으로 정한다.  
(year % 400 == 0)  
=> (year%4==0)and(year%100!=0)or(year%400)==0

```python
year = 0
year = int(input("년도 입력"))

if(((year%4==0) and (year%100!=0)) or (year%400==0)) :
    print("%d 년은 윤년입니다." %year);
else :
    print("%d 년은 윤년이 아닙니다." %year);
```  

* 실행결과  
![윤년_실행결과](https://github.com/jdaun/TIL/blob/master/MOOC/img/yoonnyeon_python.PNG)

# Ⅳ. 제어 문장 1
# WEEK 4-1 조건문(if)
## 조건문(if)
* 조건의 결과(참 또는 거짓)에 따라 프로그램의 흐름을 제어하는 문장  
* 어떠한 조건을 만족하면 그에 해당하는 일이 처리되는 문장
```python
if (expression):
    statement1 # 실행해야 할 문장은 space 또는 tab(4칸)으로 들여쓰기 해야한다.
   
next_statement
```
* 블록(Block)
  * 여러 코드가 이루는 일정한 구역
  * 파이썬의 경우, 들여쓰기로 구역을 나눔
  * 들여쓰기는 스페이스(Space)나 탭(Tab)둘다 사용 가능
  - 스페이스 4칸 사용 권장
## if else
* if에서 결과가 거짓인 경우 수행해야 할 문장이 있다면 키워드else를 사용
* 조건의 결과가 참이면 if문 바로 다음의 문장 수행, 거짓이면 else문 다음의 문장들을 수행
```python
if (expression):
    statement_true
else :
    statement_false
    
next_statement
```
## 중첩 if
```python
if 조건A :
    if 조건1 :
        수행할 문장 A1
    else :
        수행할 문장 A2
else :
    수행할 문장B
```
* 예제  
마트에서 사과가 신선하면 사과를 산다.  
만약 사과가 개당 1000원 미만이면 10개를 산다.  
하지만 사과가 개당 1000원 이상이면 5개만 산다.  
```python
appleQuality = input("사과의 상태를 입력하시오: ")
applePrice = int(input("사과 1개의 가격을 입력하시오 "))
if appleQuality == "신선":
    if applePrice < 1000:
        print("10개를 산다")
    else:
        print("5개를 산다")
else:
    print("사과를 사지 않는다")
```
## if elif
* 조건 여러 개를 비교하여 조건에 맞는 문장을 수행
```python
if 조건A :
   수행할 문장 A
elif 조건B :
   수행할 문장 B
...
else :
   수행할 문장 C
```

# WEEK 4-2 조건문 실습
## 1. 일상 생활 문제: 성적처리
학생들의 점수를 입력받아 점수에 따라 성적을 산출하는 프로그램  
## 문제 해결을 위해 필요한 것들(Computer Thinking)
* 1.성적자료를 입력 받아 변수에 저장하는 방법
  * 1.변수 선언 (python 101)
  * 2.입력 함수: input함수(int형으로 입력받기)
* 2. 점수에 따라 학점을 계산하기 위해서 필요한 연산자
  * 1. 관계 연산자: (python101 >= 90)
* 3.조건에 따라 프로그램의 흐름을 제어하는 명령어
  * 1. 조건 명령어: if else
  * 2. 여러 조건비교 명령어: if elif

```python
python101 = int(input("파이썬 점수를 입력하세요: "))
if (python101 >= 90) :
    print("학점 A")
elif (python101 >= 80) :
    print("B")
elif (python101 >= 70) :
    print("C")
elif (python101 >= 60) :
    print("D")
elif (python101 >= 50) :
    print("E")
else :
    print("파이썬 프로그래밍 학점은 F입니다.")
print("수고 많으셨습니다!")
```

## 2. 가위 바위 보 게임
P대학교 Y교수는 학생들과 가위, 바위, 보 게임을 만들기 위해 고민하고 있다.  
학생들이 가위, 바위, 보 게임을 즐길 수 있도록 컴퓨터를 활용하여 해결하고자 한다.
* 사용자가 가위, 바위, 보 중에서 하나를 선택하고 컴퓨터도 난수로 가위, 바위, 보 중에서 하나를 선택
* 사용자의 선택과 컴퓨터의 선택을 비교하여서 승패를 화면에 출력
## 문제 해결을 위해 필요한 것들(Computer Thinking)
* 1.난수 생성하기
  * 1.라이브러리 함수 활용(import random)
* 2. 사용자 선택 변수를 입력 받아 변수에 저장하는 방법
  * 1.변수 선언(player)
  * 2.입력함수: input함수
* 3. 조건에 따라 난수 생성하기
  * 1.난수 함수 활용(number = random.randint(0,2))
* 4. 생성된 난수를 활용하여 가위바위보 게임 알고리즘 만들기
  * 1.게임규칙에 따라 알고리즘 만들기
  * 2.여러 조건에 따라 수행되는 문장 만들기(if elif)
 
```python
import random

number = random.randint(0,2)
player = input("(가위,바위,보)중에서 하나를 선택하세요: ")
if (number == 0) :
    computer = "가위"
elif (number == 1) :
    computer = "바위"
else :
    computer = "보"
print("사용자: ",player,"컴퓨터: ",computer)

if (player == computer):
    print("비겼음")
elif (player == "가위"):
    if (computer == "바위"):
        print("컴퓨터가 이김")
    else:
        print("사용자가 이김")
elif (player == "바위"):
    if (computer == "보"):
        print("컴퓨터가 이김")
    else:
        print("사용자가 이김")
elif (player == "보"):
    if (computer == "가위"):
        print("컴퓨터가 이김")
    else:
        print("사용자가 이김")
 ```
