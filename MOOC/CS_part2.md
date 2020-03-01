# [MOOC - Computer Science(컴퓨터공학 입문) Ⅱ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC104+P2001/about)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용하여 일상 생활에 주어진 문제를 해결할 수 있도록 프로그래밍 기본 원리와 개념을 이해한다.  
문제 해결을 위해 C 언어로 프로그래밍 언어의 기본 구조와 문법을 알고, 그 문법으로 해결할 수 있는 다양한 일상 생활의 문제를 예제를 통해 학습한다.  

# 목차
* [Ⅴ. 조건문](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part2.md#%E2%85%B4-%EC%A1%B0%EA%B1%B4%EB%AC%B8)
  * [조건문(if)](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part2.md#week-5-1-%EC%A1%B0%EA%B1%B4%EB%AC%B8if%EA%B3%BC-%EB%AC%B8%EC%A0%9C%ED%95%B4%EA%B2%B0-%EC%98%88%EC%A0%9C%EC%84%B1%EC%A0%81%EC%B2%98%EB%A6%AC)
  
# Ⅴ. 조건문 
# WEEK 5-1 조건문(if)
## 조건문(if)
* 조건의 결과(참 또는 거짓)에 따라 프로그램의 흐름을 제어하는 문장
* 어떠한 조건을 만족하면 그에 해당하는 일이 처리되는 문장
```c
if (expression)
   statement1;
next_statement;
```

* if에서 결과가 거짓인 경우 수행해야 할 문장이 있다면 키워드 else를 사용
```c
if (expression)
{
   statement_true;
}
else
{
   statement_false;
}
next_statement;
```

* else if
  * 조건 여러 개를 비교하여 조건에 맞는 문장을 수행
  * 중첩된 if문에서 else이후에 if문을 실행하는 구문 이용
```c
if (expression1)
{
   statement1;
}
else if(expression2)
{
   statement2;
}
else if(expression3)
{
   statement3;
}
else
{   
   statement4;
}
next_statement;
```
