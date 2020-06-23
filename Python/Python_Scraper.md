[Python으로 웹 스크래퍼 만들기](https://nomadcoders.co/python-for-beginners/lobby)을 참고하여 정리하였습니다.

## 목차
* Why Learn Python


## Why Learn Python
* 파이썬은 세계에서 가장 사랑받는 언어 중 하나로 웹개발
* GUI, Scientific and Numeric, 소프트웨어 개발, 머신러닝을 위해 사용되는 System Aministration, 데이터 시각화, Data Science에 사용
* 구글크롬으로 진행
* (The Python Standard Library)[https://docs.python.org/3/library/]
파이썬이 어떻게 동작하는지 알 수 있음
* 리스트(List)
값 생성, 삭제, 수정이 가능하다.
```python
days = ["Mon", "Tue", "Wed", "Thur", "Fri", "Sat"]
```
* 튜플(Tuple)
리스트와 다르게 값을 바꿀 수 없다.
```python
days = ("Mon", "Tue", "Wed", "Thur", "Fri", "Sat")
```
* 딕셔너리(Dicts)
Key, Value를 한 쌍으로 갖는 자료형  
순차적으로 해댱 요굿값을 구하지 않고 Key를 통해 Value를 얻음
```python
dic = {'name': 'nico', 'age': 6, 'fav':['kimchi', 'sashimi']}
```
* 함수(function)
[Built-in Function](항상 사용할 수 있는 함수)
type():  자료형 반환
int(변수명): int로 바꿔줌 

```python
def say_hello(): 
  print("hello")
  print("bye")

def p_plus(a, b):
  print(a+b)

say_hello()
p_result = p_plus(2, 3)
print(p_result) // 아무것도 리턴하지 않았으므로 None
```
파이썬은 함수의 인자의 위치 상관없이 인자의 이름에 따라 결정된다. 따라서 result = plus(b=30, a=1)도 가능  

```python

def say_hello(name, age):
  return f"hello {name} you are {age} years old"
hello = say_hello("nico", "12")
print(hello)
```
해당 변수 이름의 값을 가져오는 방법은 두가지가 있다.
위가 1. String을 formatting하는 방법: {name}, {age} 실제 변수 이름
2. 문자열 끼리 +를 이용하여 문자열을 합칠 수 있다.

* keyword argument
인자 순서대로 하지 않아도 인자값을 정할 수 있다.





