# [MOOC - Computer Science(컴퓨터공학 입문) Ⅱ](https://pabi.smartlearn.io/courses/course-v1:POSTECH+DSC104+P2001/about)  
이 문서는 위 MOOC강의를 듣고 필기용으로 기록되었습니다.  
[Part1강좌](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part1.md)에 선행되는 과정입니다.

# 개요
컴퓨터를 활용하여 일상 생활에 주어진 문제를 해결할 수 있도록 프로그래밍 기본 원리와 개념을 이해한다.  
문제 해결을 위해 C 언어로 프로그래밍 언어의 기본 구조와 문법을 알고, 그 문법으로 해결할 수 있는 다양한 일상 생활의 문제를 예제를 통해 학습한다.  

# 목차
* [Ⅴ. 조건문](https://github.com/jdaun/TIL/blob/master/MOOC/CS_part2.md#%E2%85%B4-%EC%A1%B0%EA%B1%B4%EB%AC%B8)
  * [조건문(if)과 문제해결 예제(성적처리)]()
  * [조건문(switch)과 문제해결 예제(윤년계산)]()
  
# Ⅴ. 조건문 
# WEEK 5-1 조건문(if)과 문제해결 예제(성적처리)
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

# WEEK 5-2 조건문(switch)과 문제해결 예제(윤년계산)
## switch
* 선택해야 할 조건이 여러 개 있을 경우 조건에 맞는 문장을 선택하여 수행
* expression, value: 정수 또는 정수 수식이어야 함
* switch case: 필수 항목
* break, default: 선택 항목
```c
switch (expression)
{
   case value1 :
      statement1;
      break;
   case value2 :
      statement1;
      break;
   default :
      statement;
      break;
}
next_statement;
```
* switch의 값을 case상수식과 차례로 비교하여 값과 일치하는 case문장을 수행하고 break문을 만나면 swtich문을 종료
* break문을 지정하지 않으면 최초로 break문이 나올 때까지 현재 실행된 문장 이후의 모든 상수식의 문장들을 실행

## 일상 생활 문제 해결: 윤년(leap year)
* 2월을 제외하고 1~12월의 마지막 날짜는 정해져 있다.
  * 31일: 1,3,5,7,8,10,12
  * 30일: 4,6,9,11
* 2월의 마지막 날이 어떤 해는 28일, 어떤 해는 29일인 경우가 있는데 년과 월을 입력했을 때 해당하는 월의 마지막 날짜를 알고 싶다면?
  * 2월 마지막 날은 윤년 계산 결과가 필요함
* 윤년을 계산하는 방법 조사하기(치윤법)
  * 기원 연수가 4로 나누어 떨어지는 해는 우선 윤년으로 하고, (year % 4 == 0)
  * 그 중에서 100으로 나누어 떨어지는 해는 평년으로 하며, (year % 100 != 0)
  * 다만 400으로 나누어 떨어지는 해는 다시 윤년으로 정한다.(year % 400 == 0)
  * => (year % 4 == 0) && (year % 100 ! = 0) || (year % 400 == 0)
```c
#include <stdio.h>

int main(void) {
int year = 0, month = 0, maxDay = 0;
printf("\n년과 월을 입력하세요: ");
scanf("%d %d", &year, &month);
switch(month){
	case 1:
	case 3:
	case 5:
	case 7:
	case 8:
	case 10:
	case 12:
		maxDay = 31;
		print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
		break;
	case 4:
	case 6:
	case 9:
	case 11:
		maxDay = 30;
		print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
		break;
	case 2:
		if ((year % 4 == 0) && (year % 100 != 0) || (year % 400 == 0))
		{
			maxDay = 29;
			print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
			break;	
		}
		else
		{
			maxDay = 28;
			print("%d년 %d월 말 일은 %d일 입니다.\n", year, month, maxDay);
			break;
		}
	default:
		print("입력이 잘못 되었습니다.\n");
	}
	return 0;
}
```



