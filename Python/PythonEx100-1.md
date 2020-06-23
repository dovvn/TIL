## Python 100제 1부

제주 코딩 베이스 캠프 Python 100제 1부를 풀고 오답을 기록했습니다.  

## 15번
```python
n = input()
print('안녕하세요. 저는 {}입니다.' .format(n))
```
#### 파이썬 문자열 포매팅 4가지 방법: 문자열에 변수를 넣는 방식  
  * %d, %f, %s 활용
  데이터타입을 신경써야 하므로 불편함
  ```python
  a = 5
  b = 8
  fmt1 = '%d x %d = %d'%(a,b,a*b)
  print(fmt1)
  ```
  * '{}'.format() 활용
  ```python
  a = 5
  b = 8
  fmt2 = '{} x {} = {}'.format(a,b,a*b)
  print(fmt2)
  ```
  
  * '{변수명}'.format(변수명=값)활용
  ```python
  a = 5
  b = 8
  fmt3 = '{a} x {b} x {c}'.format(a=a, b=b, c=a*b)
  print(fmt3)
  ```

* f-스트링: f'{변수}'활용 - 매우 편함!★
```python
a = 5
b = 8
fmt4 = f'{a} x {b} = {a*b}'
fmt4 = f'{a} x {b} = {a*b:4}' #자리수 추가
print(fmt4)
```
